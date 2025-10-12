+++
title = "Automatic Filtered Water Tap"
pathname = "/automatic-tap"
description = "Solution to a problem that doesn't exist..."
date = 2025-09-14
updated = 2025-10-12

[taxonomies]
tags = ["projects", "hydro", "electronics", "programming"]

[extra]
copy_button = true
+++

# Bevezető

Elegem lett a szűrt vízes csapok lassúságából, sajnos ezen nem tudok egyszerűen változtatni. Eszembe jutott hogy ki lehet kerülni a problémát, ha automatizálom a kancsó töltését. Meglett az alapötlet, veszek egy kancsót és építek egy olyan csapot, ami alá be tudom rakni, az automatikusan érzékeli és teljesen feltölti.

## Ötletelés

El is mentem az IKEA-ba, hogy keressek inspirációt a dizájnra, ekkor megláttam a [TVÄRHAND](https://www.ikea.com/hu/hu/p/tvaerhand-asztali-lampa-fekete-bambusz-90510894/) lámpát, a minimalista tartókarja nagyon megtetszett, és a bambusz alap is, azonban a talp nem felelt volna meg a mérete miatt. Tovább keresgéltem talpnak valót, meg is találtam a [FASCINERA](https://www.ikea.com/hu/hu/p/fascinera-vagodeszka-akac-00503360/) vágódeszkát, melynek a formája nagyon megtetszett, és ideális is volt. Az elképzelésem a következő:
![image_2025-09-14T13-12-30Z.png](/blog/automatic-tap/image_2025-09-14T13-12-30Z.png)
A szürke karika a kancsó helye, a fekete pedig csap alja lesz.

## "Automatikus"

De hogyan ismeri fel a kancsót a csap, és honnan tudja mennyit töltsön bele? Első megoldás az NFC olvasó a csap aljában és egy NFC matrica a kancsó alján, ennek segítségével felismerhető a kancsó, de ez nem oldja meg a mennyiség problémát. Mivel dizájn okokból nem lehet egy vízérzékelőt rárakni a csap fejére, a legegyszerűbb megoldás egy mérlegcellát használni a csap alatt, így azonban a kancsó helyénél ki kell vágni a talpat, és külön rárakni a kivágást a mérlegcellára. Minden vezérlést a csapon kívül a vízszűrő mellett elhelyezett doboz fog végezni, a talpban csak egy mérlegcella, egy erősítő és egy nfc olvasó lesz.

## Csatlakozás

A vízszűrő 1/4 colos csövezést használ, szerencsére minden kiegészítőt meg tudtam venni az [eltetoviz.hu](https://www.eltetoviz.hu/)-n. A szelep funkciót egy [mágneses szelep](https://eltetoviz.hu/webaruhaz/szerelekek/elzarok-szelepek/m%C3%A1gnes-szelep-gyorscsatlakoz%C3%B3val-24v.html) látja majd el, amelyet egy ESP8266 mikrovezérlő kapcsol majd egy relé által. A lámpakar belseje 7mm, az előző projektemből megmaradt 4x5mm-es élelmiszeripari szilikoncső kényelmesen belefér. 