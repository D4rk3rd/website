+++
title = "Tobacco Shop Compass"
pathname = "/tobacco-compass"
description = "Tobacco compass?"
date = 2025-10-09
updated = 2025-10-12

[taxonomies]
tags = ["projects", "compass", "electronics", "programming"]

[extra]
copy_button = true
+++

# Bevezető

to be written...

<!-- toc -->
# Adatbázis

Mivel nincs publikus adatbázis tökéletes formában előre elkészített adatokkal (gondoltam ezt én akkor...), ezért a legegyszerűbb megoldásnak az tűnt, hogy összescrapeljek egyet magamnak.
Sokfajta dohánybolt kereső van az interneten, de a legmegbízhatóbbnak a [Nemzeti Dohánybolt Kereső](https://nemzetidohanyboltkereso.hu/) tűnt, leírásuk szerint 2013 óta gyűjtik az adatokat, több mint 4500 bejegyzett cím áll rendelkezésükre.
Ez mind szép és jó, de hogy szerzem meg ezeket az adatokat?

## Első koncepció

Első gondolatom az üres keresés volt, amely gyengébben megírt oldalak esetén visszadobja az összes passzoló adatbázis-rekordot (amely az összes), és ha letöltöm az oldalt akkor a HTML-ből kikaparhatom az adatot, azonban ez esetben ez nem vált be, mert az oldal csak 20 címet adott vissza. Basszus.

Második gondolat: Mivel az ország négyszámjegyű irányítószámokra van felosztva, ezért (feltételezve persze hogy egy irányítószámban nincs több mint 20 dohánybolt) egyenként rákereshetek az irányítószámokra, és lementhetem az oldalt, majd úgy összekaparhatok egy adatbázist. Ez lehetségesnek tűnik, álljunk is bele.

### Kivitelezés

Először is megnéztem hogy a weboldal válaszol-e a wget-re User-Agent header változtatás nélkül:

```bash
❯ wget "https://nemzetidohanyboltkereso.hu/" -S
Resolving nemzetidohanyboltkereso.hu (nemzetidohanyboltkereso.hu)... 92.43.203.166
Connecting to nemzetidohanyboltkereso.hu (nemzetidohanyboltkereso.hu)|92.43.203.166|:443... connected.
HTTP request sent, awaiting response... 
  HTTP/1.1 200 OK
```

Siker! A kidobott file szerencsére nem egy üres HTML, és tartalmazza az értékes adatokat.
Rendben, szóval ez működik. A következő lépés az automatizálás. A magyarországi irányítószámok egy kereséssel [letölthetők az internetről](https://www.szallitmanyozas.hu/deu/data/iranyitoszamok.xls), pici tisztogatás és duplikáció törlés után készen áll a felhasználásra.

### A Scraper

Kell egy program, ami végigiterál a `zips.csv` fájlon, minden irányítószámnál lekéri a weboldalt vele, mint keresési argumentummal (`https://nemzetidohanyboltkereso.hu/?s={irányítószám}`).
Erre írattam egy [shell scriptet](https://github.com/D4rk3rd/tobacco-compass/blob/master/old_scraper/downloader.sh), ami pont ezt csinálja, ez 3 óra alatt letöltötte az összes keresést.

### Post processing

Azután a HTML fájlokból kinyerem a linket, címet, és várost, összegyűjti egy CSV-be (ez végül több mint 4400 sor lett), és minden egyes címhez rendel koordinátákat. Ehhez [OpenStreetMap Golocation API](https://nominatim.org/)-t használtam, így is azonban több mint 5 órába telt (tiszteletben tartva az ingyenes API kérési rátát) és kb. 500 cím üresen maradt. Ezeknél többek között helyrajzi szám, emelet, házszám hiánya, elírás okozta a kimaradást, és nem volt kedvem egyenként manuálisan kikeresni a helyes koordinátákat.
Ezután megnéztem párat szúrópróba szerűen és észrevettem, hogy van aminek a közelében sincs dohánybolt. Ezen a ponton feladtam, biztos van jobb megoldás, így vissza az elejére.

## Második koncepció

Mivel az előző nem vált be, keresni kell egy egyszerűbb megoldást. Még több keresés után megtaláltam [ezt az oldalt](http://www.dohanyboltok.net/), ahol ugyan nincs egyértelműen letölthető adat, de egy embedded Google Maps térkép elmondja, hogy az adatok kinyerése triviális. Kis körbenézés után meg lehet találni a `markers` JavaScript objektumot, amely nem csak a címét tartalmazza az összes Maps pinnek, de döntő részénél a koordinátákat is!
Tökéletes, egy fetch request és már meg is van a weboldal kódja, amely tartalmazza a `markers` objektumot. Szuper, kis Regex és egy [Python script](https://github.com/D4rk3rd/tobacco-compass/blob/master/db_builder/builder.py) és kevesebb mint 5 másodperc alatt nem csak kész a lista, de használatra kész a formázása is.

A 6270 bejegyzett címből 5979-hez van kötve koordináta, ami nekem elég jó, persze ezeknél is el lehetne játszani az előbb használt geolocation scriptet egy kis módosítással.
