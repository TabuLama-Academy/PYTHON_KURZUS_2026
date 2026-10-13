# Terminálkezelés – 40 gyakorlófeladat Pythonban

**Tanulói feladatlap | 12. évfolyam | Öt nehézségi szint**

## Útmutató

A feladatok célja **a feladatszöveg alapján felismerni**, milyen terminálos kiírási műveletet kell választani.

- A bemutatott változókat/listákat használd, azokat nem kell bekérni.
- A megoldás **egyszerű Python-kód** legyen: `print()`, f-string, ciklusok és szükség esetén feltételek.
- Ne használj osztályokat, külső csomagokat vagy HTML-kimenetet.
- A képernyőképet helyettesítő `text` blokkok **elvárt kimenetek**, nem megoldáskódok.
- A feladat mindenütt írja le a kívánt **megjelenítést**, de nem mondja meg, milyen Python-szintaxissal valósítsd meg.
- Mindig döntsd el először: **mit**, **milyen sorrendben**, **milyen elválasztóval**, **hány sorban**, **milyen igazítással** kell kiírni.

A számozás: 1.1–1.8 alapok; 2.1–2.8 szövegformázás; 3.1–3.8 számformázás; 4.1–4.8 összetett kiírás; 5.1–5.8 haladó (opcionális).

---

# 1. szint – A `print()` lehetőségei

## 1.1. Üdvözlőszöveg

Írj programot, amely a terminálra kiírja az alábbi üzenetet!

~~~text
Üdvözöllek a Python kurzuson!
~~~

## 1.2. Tanulói adatok

Adott: `nev = "Anna"`, `kor = 18`, `osztaly = "12.A"`. Írd ki őket **egyetlen sorban**, pontosvesszőkkel elválasztva!

~~~text
Anna;18;12.A
~~~

## 1.3. Termékadatok

Adott: `termek = "Füzet"`, `ar = 850`, `db = 3`. A három érték között pontosan ` | ` szerepeljen!

~~~text
Füzet | 850 | 3
~~~

## 1.4. Betöltési üzenet

Két egymást követő kiírásból jelenítsd meg az alábbi szöveget **ugyanabban a sorban**!

~~~text
Feldolgozás... Kész!
~~~

## 1.5. Több sor egyetlen szövegből

Egyetlen kiírási utasítással jelenítsd meg három külön sorban a következőt!

~~~text
Hétfő
Kedd
Szerda
~~~

## 1.6. Tabulátorral elválasztott adatok

Adott a `"Név"`, `"Kor"`, `"Átlag"` fejléc. Írd ki ezeket egy sorban **tabulátorokkal elválasztva**, majd alá a `"Anna"`, `18`, `4.5` értékeket, ugyanilyen elválasztással!

Megjegyzés: a feladat nem kíván meg rögzített oszlopszélességet.

## 1.7. Speciális karakterek

Jelenítsd meg a következő két sort. Az első tartalmazzon idézőjeleket, a második Windows-útvonalat!

~~~text
A könyv címe: "Python alapok"
Mappa: C:\Kurzus\Python
~~~

## 1.8. Elválasztó és cím

Készíts 30 kötőjelből álló vonalat, majd a `TERMINÁLKEZELÉS` címet és ismét 30 kötőjelet! Az elválasztó karaktereket ne gépeld le egyesével.

---

# 2. szint – Szövegek igazítása

## 2.1. Balra igazított név

Adott: `nev = "Anna"`. Jelenítsd meg a nevet egy **15 karakter széles mezőben, balra igazítva**. Tegyél `|` karaktert közvetlenül a mező elejére és végére, hogy az üres helyek is látszódjanak!

~~~text
|Anna           |
~~~

## 2.2. Jobbra igazított név

Ugyanezt a nevet jelenítsd meg egy 15 karakter széles mezőben, de **jobbra igazítva**!

~~~text
|           Anna|
~~~

## 2.3. Középre igazított cím

Adott: `cim = "PYTHON"`. A címet egy 20 karakter széles mező **közepére** helyezd. A mezőt `|` karakterek határolják!

## 2.4. Csillagokkal kitöltött cím

Adott: `cim = "MENU"`. Jelenítsd meg 20 karakter széles mező közepén úgy, hogy a fennmaradó helyet `*` jelek töltsék ki!

## 2.5. Nevek egységes oszlopban

Az alábbi listából minden nevet külön sorba írj ki, **ugyanakkora, 15 karakter széles, balra igazított** mezőbe. Mindegyik sor a `|` karakterrel záruljon.

~~~python
nevek = ["Anna", "Benedek", "Kata", "Alexandra"]
~~~

## 2.6. Kétoszlopos lista

Adott:

~~~python
tanulok = [
    ["Anna", 18],
    ["Benedek", 17],
    ["Kata", 19]
]
~~~

Írj `Név` és `Kor` fejlécű táblázatot! A név **15 karakter széles, balra igazított**, a kor **5 karakter széles, jobbra igazított** mezőben jelenjen meg. A fejléc és az adatsorok azonos formátumúak legyenek.

## 2.7. Rövidített azonosítók

Adott:

~~~python
azonositok = ["ABC123456", "XYZ987654", "DEF555111"]
~~~

Mindegyikből csak az **első 5 karaktert** írd ki, külön sorban!

~~~text
ABC12
XYZ98
DEF55
~~~

## 2.8. Állítható szélességű oszlop

Adott: `szelesseg = 25` és `nev = "Anna"`. A név a változó által meghatározott szélességű, **balra igazított** mezőben jelenjen meg; a mezőt határolja két `|` karakter. Ha a szélesség 30-ra változik, a kódban ne kelljen a formátumszöveget átírni!

---

# 3. szint – Számformázás

## 3.1. Tanulmányi átlag

Adott: `atlag = 4.567`. A számot **pontosan két tizedesjeggyel** jelenítsd meg!

~~~text
Tanulmányi átlag: 4.57
~~~

## 3.2. Különböző pontosságok

Adott: `pi = 3.14159265`. Írd ki három sorban **egészre formázva**, **két tizedesjeggyel**, majd **négy tizedesjeggyel**!

## 3.3. Háromjegyű sorszámok

Adott a `[1, 7, 24, 103]` lista. Minden számot külön sorba írj úgy, hogy **legalább három számjegyből álljon**, a hiányzó helyeken nullával!

~~~text
001
007
024
103
~~~

## 3.4. Nagy összegek

Adott: `ar = 1234567`. Írd ki az összeget forintban, **ezres csoportokban, szóközökkel elválasztva**!

~~~text
Ár: 1 234 567 Ft
~~~

## 3.5. Százalékos eredmény

Adott: `teljesitmeny = 0.875`. Az eredményt **százalékban, egy tizedesjeggyel** jelenítsd meg!

~~~text
Teljesítmény: 87.5%
~~~

## 3.6. Pozitív és negatív változás

Adott: `valtozasok = [12, -5, 0]`. Írd ki a számokat külön sorban úgy, hogy a pozitív szám előtt **pluszjel** is szerepeljen!

~~~text
+12
-5
+0
~~~

## 3.7. Tudományos jelölés

Adott: `meres = 12500`. A számot **tudományos jelöléssel és két tizedesjeggyel** írd ki!

~~~text
1.25e+04
~~~

## 3.8. Pénztárbizonylat

Adott:

~~~python
arak = [850, 1999, 12000]
~~~

Mindegyik árat külön sorba írd ki **8 karakter széles, jobbra igazított mezőben**, utána egy szóközzel és a `Ft` jelöléssel. Az összegek egy oszlopba igazodjanak.

---

# 4. szint – Táblázatok, riportok, több adatsor

## 4.1. Egyszerű névsor

Adott:

~~~python
nevek = ["Anna", "Benedek", "Kata"]
~~~

Írj `NÉVSOR` címet, alá 25 kötőjelből álló elválasztóvonalat, majd a neveket külön sorokban, számozva `1. Anna`, `2. Benedek` stb. formában!

## 4.2. Osztályzatok táblázata

Adott:

~~~python
tanulok = [
    ["Anna", 5],
    ["Péter", 4],
    ["Kata", 3]
]
~~~

Készíts fejlécet és adatsorokat. A `Név` oszlop **15 karakter széles és balra igazított**, a `Jegy` oszlop **5 karakter széles és jobbra igazított** legyen!

## 4.3. Pontszám és átlag

Adott:

~~~python
eredmenyek = [
    ["Anna", 87.535],
    ["Péter", 72.0],
    ["Kata", 99.876]
]
~~~

Készíts kétszlopos táblázatot, ahol a nevek **balra**, a számok **jobbra** igazodnak, és a pontszám **két tizedesjeggyel** látszik!

## 4.4. Keretes oszlopok

Készíts a terminálban kétszlopos, `+`, `-` és `|` karakterekkel határolt táblázatot! Az első oszlop 12 karakter széles, a második 5; a `Név` és `Kor` fejléc alatt az `Anna / 18` és `Péter / 17` adatsor szerepeljen.

## 4.5. Vizsgaeredmények

Adott:

~~~python
pontok = [40, 50, 68, 92]
~~~

Minden pontszám mellett szerepeljen a `MEGFELELT` felirat, ha az érték **legalább 50**, egyébként `NEM FELELT MEG`. Minden eredmény külön sorba kerüljön, azonos szerkezettel!

## 4.6. Könyvkiadási statisztika

Adott, már kiszámított adatok:

~~~python
statisztika = [
    [2020, 45, 834005, 29, 416000],
    [2021, 49, 779130, 52, 736900],
    [2022, 63, 1115210, 42, 649639],
    [2023, 41, 625185, 40, 536000]
]
~~~

A `Év`, `Magyar kiadás`, `Magyar példányszám`, `Külföldi kiadás`, `Külföldi példányszám` fejlécek alatt jelenjenek meg az adatok **egyforma oszlopkezdettel**. A számokat jobbra igazítsd!

Ez a feladat csak a **megjelenítésre** koncentrál: nem kell fájlt beolvasni vagy újra statisztikát számolni.

## 4.7. Egyszerű oszlopdiagram

Adott:

~~~python
pontok = [
    ["Anna", 30],
    ["Péter", 15],
    ["Kata", 40]
]
~~~

A név után jelenjen meg egy `#` karakterekből álló diagram: **minden 5 pont után 1 jel**. A neveket balra igazítsd, hogy a diagramok egymás alatt kezdődjenek!

Elvárt jelhosszúságok: Anna 6, Péter 3, Kata 8.

## 4.8. Napi összesítő

Adott:

~~~python
eladasok = [
    ["Hétfő", 12500],
    ["Kedd", 8500],
    ["Szerda", 21000]
]
~~~

Készíts `HETI BEVÉTEL` címet, elválasztóvonalat, napokra bontott, rendezett táblázatot és a végén az összes bevételt! Az összegek **szóközös ezres csoportosítással** és `Ft` jelöléssel jelenjenek meg.

---

# 5. szint – Haladó terminálos megjelenítés (opcionális)

**Megjegyzés:** a színezés és a sorfrissítés támogatása terminálonként eltérhet. A dátumok formázásához a Python beépített `datetime` modulja használható.

## 5.1. Sikeres üzenet

Az `SIKERES MŰVELET` üzenetet **zöld színnel** jelenítsd meg, majd állítsd vissza a terminál színét!

## 5.2. Hibajelzés

A `HIBA` szó **piros**, a következő `Próbáld újra!` üzenet **normál színű** legyen!

## 5.3. Középre igazított menü

Készíts egy 30 karakter széles, vízszintes vonalakkal határolt menüt. A `FŐMENÜ` felirat középre igazítva jelenjen meg, alatta a `1. Listázás`, `2. Keresés`, `0. Kilépés` menüpontokkal.

## 5.4. Dátumformátum

Adott dátum: 2026. október 13. A beépített dátumkezelés segítségével jelenítsd meg így:

~~~text
2026.10.13
~~~

## 5.5. Egysoros folyamatjelző

Írj programot, amely egy terminálsoron mutatja a `Feldolgozás: 10%`, majd `Feldolgozás: 50%`, végül `Feldolgozás: 100%` állapotot. A korábbi százalék helyére kerüljön az új érték.

## 5.6. Színnel jelzett pontszám

Adott: `pontok = [28, 55, 91]`. A 50 alatti eredmények **piros**, az 50 vagy nagyobb eredmények **zöld** színnel jelenjenek meg. Az eredmény soronként, százalékjellel szerepeljen!

## 5.7. Névvel ellátott karakterdiagram

Adott:

~~~python
adatok = [["A", 4], ["B", 7], ["C", 2]]
~~~

Készíts vízszintes sávdiagramot, amelyben az adatok mellett a megfelelő számú `#` jelenik meg. A sávok azonos pozíción kezdődjenek!

~~~text
A | ####
B | #######
C | ##
~~~

## 5.8. Összetett konzolos jelentés

Adott:

~~~python
tanulok = [
    ["Anna", 87.5],
    ["Péter", 48.0],
    ["Kata", 91.25]
]
~~~

Készíts `VIZSGAEREDMÉNYEK` feliratú, elválasztóvonalas, oszlopokra igazított jelentést. A nevek **balra**, a százalékok **jobbra** igazodjanak, a számok **két tizedesjeggyel** jelenjenek meg. A `MEGFELELT` / `NEM FELELT MEG` feliratot 50%-os határ alapján jelenítsd meg. Haladó változatban a minősítést színezd is!

---

## Önálló ellenőrzés minden feladat után

1. A kiírt értékek megegyeznek a megadottakkal?
2. A sorok és az elválasztójelek megfelelnek a feladatnak?
3. Az oszlopok akkor is helyesen igazodnak, ha más hosszúságú adatot írunk ki?
4. A számoknál megvan az előírt tizedesjegy, százalékjel, előjel vagy nulla?
5. Ha több adatsor szerepel, valóban ugyanaz a formátum ismétlődik?
6. Meg tudom **magyarázni**, hogy a feladat szövege melyik része indokolja a választott utasítást?

**Tanári megjegyzés:** a feladatokhoz szándékosan nincs azonnal mellékelve kész megoldás. A gyakorlás célja, hogy a tanuló maga jusson el a szöveges követelménytől a megfelelő Python-formázási műveletig. A haladó 5. szint kiegészítő; az első négy szint az alapfoglalkozásokhoz és érettségi előkészítéshez javasolt.
