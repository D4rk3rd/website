+++
title = "Cloudflare Secure Contact File Hosting"
pathname = "/cf-file-hosting"
description = "99% Scraper-proof"
date = 2025-11-19

[taxonomies]
tags = ["selfhosting", "code", "software", "cloudflare", "programming"]

[extra]
copy_button = true
+++
# Hosting a file fully on Cloudflare, and making it only accessible with a key
I would like to make a business card with an NFC tag, but I don't have tags with a storage big enough to fit a full VCard contact, and I would like the possibility to change the contact contents on the fly, whithout reprogramming the NFC tag every time, so I settled for hosting it online.
By having a direct URL to the file, it's just as easy for scrapers to download the file and stealing my info (for example when I set this up it got 300 requests just from scrapers, because they automatically noticed the change in the DNS records), as it is for anyone with the link, so by implementing a **key** in the URL adds a layer of security.
# 1. Step: Add an S2 bucket to Cloudflare.
Cloudflare includes a free 10GB of S2 storage in their free plan, which is plenty for a VCF file. The S2 bucket content can be accessed by the Worker using Bindings, never exposing any data to the open internet.

1. In the main Cloudflare Dashboard go to **Storage & databases**
2. In there, click **R2 object storage** -> **Overview**
3. Click **+ Create Bucket**
4. Bucket name can be anything, leave everything as is.
5. Next, upload the **contact.vcf** file you created (I used [this page](https://opensourcetoolkit.com/vcf))

# 2. Step: Set up a worker
To actually host and handle the key checking part of the whole operation, we will use a worker. As said before, they can directly integrate an S2 bucket, and can read secret variables.

1. In the side menu find **Compute & AI** -> **Workers & Pages**
2. Once there, click on the **Create application**
3. Select the **Start with Hello World!** option and name the worker.
4. Replace the **worker.js** file contents with the following code:

```js
export default {
  async fetch(request, env) {
    const url = new URL(request.url);

    const clientKey = url.searchParams.get("key");
    const expectedKey = env.DOWNLOAD_KEY;

    if (!clientKey || clientKey !== expectedKey) {
      return new Response("Forbidden", { status: 403 });
    }
    
    const obj = await env.MY_BUCKET.get("contact.vcf");

    if (!obj) {
      return new Response("File not found", { status: 404 });
    }

    return new Response(obj.body, {
      status: 200,
      headers: {
        "Content-Type": "text/vcard; charset=utf-8",
        "Content-Disposition": "attachment; filename=contact.vcf",
        "Cache-Control": "no-store",
      },
    });
  },
};
```

This code basically checks the incoming **GET** request, and if it doesn't have the key parameter, or if it doesn't match the one stored in the Worker Secret variable, which we will set up in a moment, it will throw a **403 Forbidden**.

# 3. Step: Configuring Worker Secrets
Great, but the Worker still has no idea what the **env** variables are, we need to set them up.
1. Head over the the **Settings** tab of your worker.
2. Under **Variables and Secrets** add a variable.
3. The variable type is **Secret**, the name is **DOWNLOAD_KEY**, and the value will be the string you want to use to access the file, like **super-secret-string**.
4. Now navigate to the **Bindings** tab, click **Add binding +**, there select **R2 bucket** and click **Add binding**.
5. For the variable name use **MY_BUCKET**, and select your previously created bucket from the list.

That's it! You're all set, to try it click on the blue **🌐 Visit** button and it will take you to the site where its hosted. You will now see **Forbidden** on the screen, that means the key wasn't sent in the HTTP request. To see if it works, send **?key=super-secret-string** (where "super-secret-string" is the string you set in the **DOWNLOAD_KEY** variable). The final request will look something like this:
`https://worker-name.accountname.workers.dev/?key=<super-secret-string>`

If all goes well you should see a download for a **contact.vcf** file, the HTTP status code should be **200 OK**.
You can try it on your phone, instead of downloading a file it will automatically prompt you to add the contact to the contact list.

Great! You can now link this URL with the key on a QR code on your business card, or use a cheap NFC sticker to hold the URL, so people can easily get your contact info with just a tap.

With a bit of modification this script is easily usable for hiding a full contact page with all the info embedded into it.
# Using a custom domain
To use a custom domain to host the file, you can:
1. Navigate to the **Setting** tab, where you can select **Domains & Routes**.
2. Click **+ Add**, and here you can either choose a **Custom domain**, or a **Route**, which maps an inbound HTTP request to the worker [using Routes](https://developers.cloudflare.com/workers/configuration/routing/#matching-behavior).
3. You can choose to disable the **worker-name.accountname.workers.dev** domain in the **Domains & Routes** pane.

You can now access the file through your own domain like so:
`https://<own-domain.tld>/?key=<super-secret-string>`