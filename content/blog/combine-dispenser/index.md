+++
title = "Combine Drink/Shot Dispenser"
pathname = "/combine-dispenser"
description = "Why did i do this?"
date = 2025-05-08
updated = 2025-10-12

[taxonomies]
tags = ["projects", "drinks", "hydro", "electronics", "programming"]

[extra]
copy_button = true
+++

![done_intro.gif](/blog/combine-dispenser/done_intro.gif)

# Bevezető

Ez a projekt a tiszta unalom szülöttje, láttam egy [videót tiktokon](https://www.tiktok.com/@farmersweeklyofficial/video/7303492813168168224) ezer éve, amiből jött nekem is az ötlet ennek a csodaszerkezetnek a megépítéséhez. Ez nem egy egyedi ötlet, lehet ilyeneket venni [Etsyn is](https://www.etsy.com/listing/1882474140/alcohol-dispenser-combine-for-6-glasses) például (kinek van erre 130 ezer forintja, de most komolyan...), de mivel nekem megvolt otthon a legtöbb alkatrészem hozzá és a tavaszi szünet közeledésével ez egy tökéletes alkalomnak tűnt arra, hogy kifogásom legyen a tanulás elhalasztásához. Ez nem egy tutorial, pusztán leírom az elkészítése lépéseit és a gondolatmenetem.

# Kell egy kombájn

Hm. Jó ötlet, el is mentem a Regiojátékba es alig hittem a szememnek, de megtaláltam [ugyanazt a kombájnt](https://www.regiojatek.hu/termek-50388-aratogep.html) amit a videóban használtak. 4000 Ft? Hülyének is megéri. Gondoltam egyszerű lesz, belerakok egy szervót az [ürítőcsiga](https://www.agraroldal.hu/szerkezet-2.html) kifele irányba való mozgatására meg egy pumpát a folyadék mozgatására.

# Jóó, hogy lehetne ezt motorizálni?

Sajnos amikor elkezdtem ezt a projektet nem volt a fejemben hogy írok is róla majd, ezért nincs képem az eredeti megoldásról amit a tervezők használtak a kombájn tervezésekor, de egyből rájöttem hogy nagyobb fejfájás lesz mint amire számítottam.
Első dolog ami kiszúrta a szemem, hogy egyetlen egy csavar nem volt az egész kombájnban (kivéve a kerekek hajtószerkezetét, ebben volt kettő), az egész könnyen letörhető fülekkel van összenyomva. Szerintem nem kell említenem hogy pár darab már elvesztette a tartóképességét, ez van amikor a legolcsóbb játékot veszem meg...
Második: az ürítőcsiga forgási tengelye nem merőleges a talajra, ami miatt kinyitáskor a csiga egy szögben emelkedett, ez nekem nem tetszett, hiszen valaki már [talált erre megoldást fokozatosan emelkedő pohárlépcsővel](https://www.youtube.com/watch?v=m9vJQDnwHUI), de na ez azért nem túl szép.
A harmadik de nem utolsó nehezítés megint az olcsó konstrukcióból ered, hiszen az összekötés az üritőcsiga és a kombájn teste között egy egyszerű műanyag-műanyag kontaktos súrlódási rémálom volt.

# Próbáljunk maradni az eredeti megoldásnál

Legelőször megpróbálkoztam a játék eredeti forgócsukló dizájnjával, de hamar rájöttem hogy ez igy nem lesz jó, hiszen rengeteg a veszteség a műanyagok csatlakozásánál. Szóval miután ezt feladtam, elkezdtem gondolkodni a következő ötleten.
Mi lehet az a dolog, ami súrlódásmentesen engedi a benne lévő tengelyt a forgásra? Így van, át is kutattam a csapágyas dobozom és a legalján megtaláltam a tökéletes egyedet, egy mini golyóscsapágyat, nem tudom miből szereztem, ne kérdezd.
A testet kifúrtam merőlegesen az asztalra úgy, hogy a csapágy külseje belepasszolt, ezt pillanatragasztőval rögzítettem, sajnos kis mérete és elég gyenge minősége miatt rengeteg volt a csapágyban a játék. Nembaj, megoldjuk. Most következett a tengely ami belemegy. Ezt az esztergán csináltam meg, egy nagyobb feje van hogy egy kisebb 8mm-es fémcsövet merőlegesen bele tudjak helyezni, erre majd magát a csőalakú csigát rá tudom húzni, a belsejébe pedig egy 5mm-es élelmiszeripari minőségű szilikoncsövet tudok vezetni.

![image_2025-04-28T18-12-41Z.png](/blog/combine-dispenser/image_2025-04-28T18-12-41Z.png)
*A műszaki rajzot később készítettem illusztráció céljából, nem pontos minden méret*

Ez működött, első ötletem a fogaskerekes áttétel volt, lehetőleg 1:1 arányban mert a szervónak amit használok(MG995) 180 fokos a tartománya. 5 feles pohár a cél, ehhez minimum 120 fok kell. Ez nem működött, rengeteget szórakoztam vele, de sajnos nem sikerült megcsinálni.
A tengely magában nem elég stabil a csapágy korábban említett játéka miatt, ezért 3D nyomtattam egy tartót egy 3,5mm-es rézperselynek, amelyben szabadon tudott forogni a tengely. Így két ponton van már támasztva, oldalra nem tud mozogni.
Nagy hibát követtem el azonban a könyök esztergálásakor, mert arra terveztem hogy a fogaskerekek hajtsák. Miután ez nem vált be a hajtó tengely az alján túl rövidnek bizonyult a következő megoldáshoz a fejemben, amely pedig egy hajlítható szilikon cső volt a hajtás átviteléhez. Ideálisan egy [kardáncsukló](https://www.aliexpress.com/item/4000202603637.html?algo_exp_id=6377a98d-6dbb-4046-8190-7da8a1e21b4c-0&pdp_ext_f=%7B%22order%22%3A%22599%22%2C%22eval%22%3A%221%22%7D&pdp_npi=4%40dis!HUF!918.28!918.28!!!2.50!2.50!%40211b680e17458649580822766edb93!10000000771932372!sea!HU!2635498839!X&curPageLogUid=x4hOn9e08lOn&utparam-url=scene%3Asearch%7Cquery_from%3A#nav-specification) lenne a megoldás, ez Magyarországon nem kapható abban a méretben amit én kerestem, a többi alkatrészt már megrendeltem Aliexpressről, nem tudnám újra kivárni a szállítást... (viszont ezt a javítást lehet, később meg fogom ejteni)
Tehát a következő lehetőség egy szilikoncső amely összeköti a könyök tengelyét a szervó tengelyével, ehhez egy vastagabb levegőztetőcsövet használtam ami nekem ugyan volt otthon bőven, de szükség esetén akváriumboltból könnyen beszerezhető.
Az előbb említett rövidsége miatt a tengelyre nehezen tudtam úgy ráfogatni a csövet, hogy az anyag forgása miatti nyúlásának ellenálljon, de végül összedobtam egy szoritót egy darab sárgaréz szekrényalkatrészből amit találtam.

A szervónál való rögzítéséhez megint az esztergához fordultam, szerencsére találtam egy olyan menetes tengely gyűrűt, amely tökéletes volt a feladatra. Az esztergában kibővítettem a furatot úgy, hogy a szilikoncső épphogy belement. A szervó tengelyének a közepén van egy M3-as menet, amelybe az esztergán csináltam egy menetes végű tengelyt.
![image_2025-04-28T19-46-21Z.png](/blog/combine-dispenser/image_2025-04-28T19-46-21Z.png)Ezt a tengelyt menetrögzítővel a szervóba ragasztottam, a külső átmérőjére rápasszol a szilikoncső, arra a tengelygyűrű és a tengelygyűrűben a csavarral a szilikoncsövet a tengelyre fogtam. Így néz ki az elkészített mechanizmus:
![image_2025-04-28T19-51-47Z.png](/blog/combine-dispenser/image_2025-04-28T19-51-47Z.png)*Tudom hogy rossz a kép, ez van.*

# Mi most a teendő?

Amikor ezzel kész lettem már megrendeltem a hiányzó alapanyagokat Aliexpressről, de azzal amim már megvolt elkezdtem dolgozni. Milyen dolgokat tudjon? Első ötlet az volt hogy automatikusan csak afelett a pohártartó felett álljon meg a kar amelyben van pohár, erre is volt ötletem mikrokapcsolókkal, végálláskapcsolókkal, azonban sajnos nem sikerült ezta funkciót megvalósítani mert nem volt legalább 5 egyforma nyomógombom amit képes volt a pohár súlya lenyomni. Milyen kár! Nem baj ezt a funkciót is bele tudom rakni bármikor, hiszen csak egy kis GPIO bővítés a mikrovezérlőn, kicsi átrendezése a pohár alatti korongnak (erről többet egy picit később), pár sor kód és már menne is, de nem volt türelmem megvárni amíg megjönnek a gombok, ezért hagytam az egész ötletet. Majd máskor.

Szóval lesz egy kijelzőnk (elegáns és úgy néz ki tőle a projekt mintha komolyabb lenne mint valójában), egy forgókódolónk a kijelző és menürendszer irányításához, 5 db címezhető LED (Minden LED dióda külön vezérelhető, egy DATA kábel kell az összeshez), egy nyomógomb a töltés indításához, egy motorvezérlő, a szervó amiről eddig írtam, a pumpa, egy folyadékérzékelő ami jelet küld ha folyadék van a csőben, és végül még egy nyomógomb, ami majd a szerkezet hátulján lesz és a cső ürítésére lesz használatos.

Az áramkör tervezés nem nagy dolog, mint a beadandóknál itt is segít a ChatGPT, és rengeteg, de rengeteg anyag van az interneten a különböző elemek összekötésére, mindent le lehet olvasni a netről. Szóval, ha van egy alkatrészlista onnan gyerekjáték az egész.

# Milyen alkatrészeket használjunk?

A legfontosabb része az elektronikának a projekt agya lesz, a mikrovezérlő. Én nagyon szeretem az ESP vezérlők különböző szériáit, olcsóak, WiFit tudnak (van ami Bluetootht és Zigbeet is!) és piszkos sok a memória bennük. Innentől fogva két választásom volt, a Wemos D1 Mini ESP8266 vagy az ESP32 Mini S2. Az ESP8266-ből nekem van otthon pár tucat, szerettem volna azt használni azonban ennyi dolog vezérléséhez ez gyenge lesz. Az ESP32 tökéletes választásnak tűnt, USB-C csatlakozó, 4MB flash memória, ADC, SPI, I2C, és a legfontosabb: 27 GPIO pin. Mindez egy olyan lapon ami 2.5cm \* 3.5cm. Hogy tessék? ÉS CSAK 1100 Ft? Esküszöm túl jó, hogy igaz legyen, de igaz. Ja meg persze ez volt otthon.

A választott alkatrészeket levezettem az alábbi táblázatba:

| Név | Választott alkatrész | Ár | Megjegyzés |
| --- | -------------------- | --- | ---------- |
| Mikrovezérlő | [ESP32 S2 Mini](https://www.aliexpress.com/item/1005006157693055.html?utparam-url=scene%3Asearch%7Cquery_from%3Apc_back_same_best&algo_exp_id=14552637-ed00-41d0-9166-02380d612a92&pdp_ext_f=%7B%22order%22%3A%221423%22%7D&pdp_npi=4%40dis!HUF!3551.64!981.76!!!70.55!19.50!%40210390b817458721014752231e3838!12000036030571903!sea!HU!0!ABX) | 1165Ft | A WiFi egyenlőre kihasználatlan marad |
| Kijelző | [SSD1306 0.96" OLED](https://www.aliexpress.com/item/1005006501624032.html?algo_exp_id=43a3c3df-8e88-445f-9b1d-898a402b8a82-0&pdp_ext_f=%7B%22order%22%3A%222799%22%2C%22eval%22%3A%221%22%7D&pdp_npi=4%40dis!HUF!1184.55!772.25!!!23.53!15.34!%402103835c17458723323766271e6cd9!12000037447041135!sea!HU!2635498839!X&curPageLogUid=Jcvv4B6DHhOb&utparam-url=scene%3Asearch%7Cquery_from%3A) | 770Ft | Volt otthon, van vele tapasztalatom |
| Forgókódoló | [KY040](https://www.aliexpress.com/item/1005006551162496.html?algo_exp_id=a42d45f7-1618-4c61-a9b4-dff4c7550a3f-0&pdp_ext_f=%7B%22order%22%3A%222378%22%2C%22eval%22%3A%221%22%7D&pdp_npi=4%40dis!HUF!8809.36!2819.15!!!174.99!56.00!%402103849717458724344765422ee66f!12000037644212085!sea!HU!2635498839!X&curPageLogUid=i8PepIPQekKY&utparam-url=scene%3Asearch%7Cquery_from%3A) | 350Ft | Nem egy minőségi cucc de erre jó lesz, volt otthon |
| LED | [WS2812b szalag](https://www.aliexpress.com/item/1005006766819624.html?algo_exp_id=cf1bf0f1-1e33-487a-8882-317efe263e2a-0&pdp_ext_f=%7B%22order%22%3A%223158%22%2C%22eval%22%3A%221%22%7D&pdp_npi=4%40dis!HUF!1093.43!1062.22!!!21.72!21.10!%402103963717458725933334924e45f2!12000038232636554!sea!HU!2635498839!X&curPageLogUid=85gu1eHf6vLc&utparam-url=scene%3Asearch%7Cquery_from%3A) | 1050Ft | 1 méter 1050Ft, 60 LED/m, volt otthon ez is |
| Nyomógomb | Piros | 700Ft | Helyi boltban vettem, nincs link. :/ |
| Motorvezérlő | [L298N Kétcsatornás H-híd](https://www.aliexpress.com/item/1005006481952956.html) | 811Ft | Elterjedt, olcsó, könnyű vezérelni |
| Szervó | [MG995 180 fokos](https://www.aliexpress.com/item/1005006294147588.html?algo_exp_id=8f83ac64-ca9a-4446-9e09-f8940a87a7cd-1&pdp_ext_f=%7B%22order%22%3A%2262%22%2C%22eval%22%3A%221%22%7D&pdp_npi=4%40dis!HUF!558.31!558.31!!!1.52!1.52!%40211b617b17458728786785989e2b34!12000036642232023!sea!HU!2635498839!X&curPageLogUid=6ZUae3adER65&utparam-url=scene%3Asearch%7Cquery_from%3A) | 1472Ft | Volt otthon, nem a legjobb de megteszi |
| Pumpa | [12V Perisztaltikus](https://www.aliexpress.com/item/1005005712663786.html) | 13615Ft | Erről írok többet a táblázat alatt |
| Buck átalakító | [LM2596](https://www.aliexpress.com/item/1005006365697021.html) | 484Ft | DC/DC konverter 12V-ról 5V-ra |
| Folyadékérzékelő | [CFS-IR2125A-55](https://www.aliexpress.com/item/1005006016356563.html) | 1775Ft | Ezt találtam, mozgó részek és direkt kontakt nélküli |
| Nyomógomb | Fekete | 150Ft | Ürítéshez, ezt is boltban vettem |

A pumpa választása kritikus. Két opció közül választhattam: membrános és perisztaltikus. A perisztaltikus előnyei a pontos, vezérelt átfolyás, magas viszkozitású folyadékok szállítása és mindezt úgy, hogy a folyadék nem hagyja el a csövet. Igen, nincs érintkező alkatrésze a folyadékkal, a szilikoncső rugalmára hagyatkozva nyomja előre a folyadékot egyenletesen. Tökéletes, első ötlet volt hogy építek egyet, de ebbe nem akartam most bele esni, így is elég nagy munka ez az egész kombájn. Szerettem volna léptetőmotorosat az abszolút tökéletes precizitás érdekében, azonban azok nagyon drágák és nem jöttek volna meg időben. Alin egyetlen egy választásom volt 13000 Ft-ért, amelynek 0,5L/perces átfolyása van, viszont szénkefés motor hajtja. Nem baj, jó időzítéssel és PWM modulációval durván be tudom lőni a pontosságát. Igazábol most hogy írom ezt rájöttem hogy le is tudnám cserélni egy hosszú tengelyes léptetőmotorra hiszen olyan maga a tengelykialakítása a pumpának. Na ezt is majd máskor.

Következő lépés az alkatrészek összekötése, mint ahogy már említettem ez triviális, hiszen az ESP-ken rá kell keresni egy pinout-ra és minden információt le tud olvasni az ember. Még egyszerűbbé lehet tenni a feladatot a ChatGPT segítségével, hiszen ő már ki tud nekünk találni az alkatrészlistából egy ideális kötözgetést, amely az én esetemben a következő:

| Elem | Jel | ESP32 GPIO | Megjegyzés |
| ---- | --- | ---------- | ---------- |
| SSD1306 OLED kijelző | SDA (I2C adat) | GPIO 8 | Alapértelmezett I2C adatvonal |
|  | SCL (I2C órajel) | GPIO 9 | Alapértelmezett I2C órajel |
| WS2812B LED szalag | Adat | GPIO 18 | RMT támogatott, FastLED/NeoPixel-hez |
| Szervó motor | PWM jel | GPIO 17 | Használható ESP32Servo-val |
| L298N motorvezérlő | IN1 | GPIO 12 | Motorirány vezérlés |
|  | IN2 | GPIO 13 | Motorirány vezérlés |
| Forgókódoló | CLK (A) | GPIO 3 | Szükség esetén megszakítás használható |
|  | DT (B) | GPIO 4 | Szükség esetén megszakítás használható |
|  | SW (Nyomógomb) | GPIO 5 | Enkóder nyomógomb |
| Nyomógomb #1 | Digitális bemenet | GPIO 6 | Belső felhúzóellenállás + debounce |
| Nyomógomb #2 | Digitális bemenet | GPIO 7 | Belső felhúzóellenállás + debounce |
| Folyadékérzékelő | Analóg bemenet | GPIO 1 | ADC1\_CH0 — használható analogRead(1) |

Szóval, amíg megjönnek az Aliexpresses dolgok Kínából, bele is kezdtem a szoftveres részébe, avagy a kód írásába. Először a három legelső dologgal foglalkoztam, a kijelzővel, a forgókódolóval és a LED-ekkel. A kódolás része úgyis unalmas, nem részletezném. A kód elérhető ebben a Github repo-ban, Arduino IDE-ben programoztam (tudom nem a legjobb erre, de ez számomra a legismerősebb környezet és nyelv). Írok róla egy gyors összefoglalót (kicsi ChatGPT segítséggel):

# Szoftveres működés alapjai

##### 1\. Bekapcsolás

* OLED kijelző inicializálása
* WS2812 LED-ek bekapcsolása
* Encoder és bemenetek beállítása (PINMODE)

##### 2\. Menürendszer

* **4 fő menü**:
    1. Pour (öntés)
    2. Volume (térfogat kiválasztása)
    3. Glass Count (pohárszám)
    4. Tap
* **Encoder működése**:
    * Forgatás: értéknövelés/csökkentés
    * Gombnyomás: érték mentése + következő menüpontra lépés

##### 3\. Öntés gomb \(GPIO 6\)

* Gombnyomás esetén:
    * Meghívja az `onPourButtonPressed()` függvényt
    * OLED-en a Tap menü jelenik meg
    * Serial monitoron megjelenik: `"Pour button on GPIO 6 pressed!"`

##### 4\. OLED kijelző

* 200 ms-onként frissül (`updateOLED()`)
* Menüfüggő tartalom jelenik meg (Pour, Volume, stb.)

##### 5\. LED visszajelzés

* `updateGlassLEDBar()` függvény
    * Vörös LED-ek mutatják az aktuális pohárszámot