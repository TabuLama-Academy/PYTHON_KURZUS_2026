# Terminálkezelés Pythonban – A terminálra történő kiírás formázása

**Elméleti tananyag | 12. évfolyam | Python 3**

## Célkitűzés

Egy program nemcsak eredményt számol, hanem azt a felhasználó számára érthetően jeleníti meg. A feladatszöveg sokszor nem nevezi meg a Python-utasítást, hanem azt írja elő, **hogyan nézzen ki a kimenet**.

A fejezet célja, hogy a tanuló a szöveges elvárásból következtessen a szükséges kiírási módra. Minden témánál ezt a sorrendet követjük:

1. **Mit kér a feladat?** – idézhető kulcsszó vagy követelmény.
2. **Mit jelent ez a program számára?** – a megoldandó probléma.
3. **Miért ezt a Python-kódot választjuk?** – az eszköz indoklása.
4. **Mi jelenik meg?** – várt terminálkimenet.

A példákhoz nem kell objektumorientált programozás, külső csomag vagy bonyolult adatszerkezet.

---

## 1. A feladatszöveg és a megfelelő művelet kapcsolata

| Ha a feladat ezt mondja… | Erre kell következtetni… | Lehetséges megoldás |
| --- | --- | --- |
| „Írja ki!” | Meg kell jeleníteni az adatot. | `print()` |
| „A nevet és az életkort írja ki!” | Több érték jelenjen meg. | `print(nev, kor)` |
| „Pontosvesszővel elválasztva” | Az értékek közötti jel változik. | `sep=";"` |
| „Ugyanabban a sorban folytatódjon” | El kell hagyni a szokásos sortörést. | `end=" "` |
| „Külön sorokban” | Sortörést kell készíteni. | Két `print()` vagy `\n` |
| „Tabulátorral elválasztva” | Tabulátort kell tenni az értékek közé. | `\t` vagy `sep="\t"` |
| „Rendezett oszlopokban” | Meg kell adni a mezőszélességet. | f-string, például `:<15` |
| „Balra / jobbra / középre igazítva” | A mezőn belüli igazítást kell beállítani. | `<`, `>`, `^` |
| „Két tizedesjeggyel” | A szám megjelenítését formázzuk. | `:.2f` |
| „Három számjeggyel, szükség esetén nullával” | A szám bal oldalát nullával töltjük fel. | `:03d` |
| „Százalékosan” | Az arányt százalékként jelenítjük meg. | `:.1%` |
| „Táblázatosan” | Fejléc + egységes formátumú sorok kellenek. | f-string + `for` |
| „Elválasztó vonallal” | Többször ki kell írni ugyanazt a karaktert. | `"-" * 40` |
| „Színes figyelmeztetéssel” | A terminál megjelenítési módját kell módosítani. | ANSI-kódok (haladó) |

**Fontos:** a szövegből nem mindig egyetlen konkrét kód következik. Egy formázási követelményt több helyes módszerrel is teljesíthetünk. A táblázat a **választás indokát** mutatja.

---

## 2. Alapvető kiírás: `print()`

### 2.1. Egyetlen érték kiírása

**Feladatszöveg:** „Jelenítse meg a tanuló nevét!”

**Következtetés:** egy értéket kell a terminálra küldenünk, ezért a `print()` függvényt használjuk.

~~~python
nev = "Anna"
print(nev)
~~~

Kimenet:

~~~text
Anna
~~~

### 2.2. Több érték és a `sep` paraméter

**Feladatszöveg:** „A nevet, az életkort és az osztályt pontosvessző válassza el!”

**Következtetés:** három adatot írunk ki, és **a közöttük lévő elválasztót** szabályozzuk. Ezért a `sep` paramétert használjuk.

~~~python
print("Anna", 18, "12.A", sep=";")
~~~

Kimenet:

~~~text
Anna;18;12.A
~~~

A `sep` alapértéke szóköz. Más példák:

~~~python
print("A", "B", "C", sep=" - ")  # A - B - C
print(2020, 1, sep="/")        # 2020/1
print("Név", "Kor", sep="\t")    # Tabulátor az adatok között
~~~

### 2.3. A `end` paraméter – a sor végének módosítása

**Feladatszöveg:** „A második kiírás az elsővel azonos sorban folytatódjon!”

**Következtetés:** a `print()` alapértelmezetten új sort kezd a kiírás után. Ezt a viselkedést kell módosítanunk a `end` paraméterrel.

~~~python
print("Betöltés...", end=" ")
print("Kész!")
~~~

Kimenet:

~~~text
Betöltés... Kész!
~~~

**Különbség:** a `sep` az értékek **között**, az `end` a kiírás **végén** helyez el karaktereket.

### 2.4. Speciális karakterek

| Jelölés | Jelentés | Példa |
| --- | --- | --- |
| `\n` | Új sor kezdése a szövegen belül | `print("Első\nMásodik")` |
| `\t` | A következő tabulátorpozícióra lépés | `print("Név\tKor")` |
| `\"` | Dupla idézőjel a szövegben | `print("A cím: \"Python\"")` |
| `\\` | Fordított perjel kiírása | `print("C:\\Python")` |

~~~python
print("Első sor\nMásodik sor")
print("Név\tKor")
print("Anna\t18")
print("A könyv címe: \"Python\"")
print("Mappa: C:\\Python")
~~~

**Miért nem elég mindig a `\t`?** A tabulátor nem fix számú szóközt jelent. Hosszú szövegek esetén az oszlopok elcsúszhatnak, ezért precíz igazításhoz később **mezőszélességet** használunk.

### 2.5. Többsoros szöveg és karakterismétlés

**Feladatszöveg:** „Írjon ki három egymást követő sort és egy 30 karakter hosszú elválasztót!”

~~~python
print("""Első sor
Második sor
Harmadik sor""")
print("-" * 30)
~~~

A három idézőjellel több sort is leírhatunk egyetlen szövegként. A `"-" * 30` harmincszor ismétli a kötőjelet.

---

## 3. f-string: változóértékek beillesztése

### 3.1. Miért használjuk?

**Feladatszöveg:** „Írja ki, hogy Anna 86 pontot ért el!”

**Következtetés:** egy mondatba változóértékeket szeretnénk beilleszteni.

~~~python
nev = "Anna"
pont = 86

print(f"{nev} eredménye: {pont} pont")
~~~

Kimenet:

~~~text
Anna eredménye: 86 pont
~~~

Az `f` betű az idézőjel előtt lehetővé teszi, hogy a `{ }` között változók vagy kifejezések értéke jelenjen meg.

### 3.2. Mezőszélesség és igazítás

**Feladatszöveg:** „A nevet 15 karakter széles helyen, balra igazítva írja ki!”

**Következtetés:** nem csak a szöveget kell megjeleníteni: meg kell adni az érték számára fenntartott **hely szélességét és igazítását**.

~~~python
nev = "Anna"

print(f"|{nev:<15}|")  # Balra
print(f"|{nev:>15}|")  # Jobbra
print(f"|{nev:^15}|")  # Középre
print(f"|{nev:*^15}|") # Középre, * kitöltéssel
~~~

Kimenet:

~~~text
|Anna           |
|           Anna|
|     Anna      |
|*****Anna******|
~~~

| Kód | Miért ezt választjuk? |
| --- | --- |
| `:<15` | A szó balra kerüljön a minimum 15 karakter széles mezőben. |
| `:>15` | A szó a mező jobb oldalához igazodjon. |
| `:^15` | A szó középre kerüljön. |
| `:*^15` | A szó középre kerüljön, a maradék helyen csillag legyen. |

**Fontos:** a szélesség **minimum**, nem levágási határ. A hosszabb szöveg nem rövidül le magától.

### 3.3. Szöveg rövidítése

**Feladatszöveg:** „Legfeljebb az első öt karakter jelenjen meg!”

~~~python
nev = "Benedek"
print(f"{nev:.5}")
~~~

Kimenet:

~~~text
Bened
~~~

### 3.4. Változóval megadott szélesség

**Feladatszöveg:** „Az oszlop szélességét egy változó határozza meg!”

~~~python
szelesseg = 20
nev = "Anna"

print(f"|{nev:<{szelesseg}}|")
~~~

A belső `{szelesseg}` miatt a mező méretét később egyszerűen módosíthatjuk.

---

## 4. Számok formázása

### 4.1. Tizedesjegyek: `.2f`

**Feladatszöveg:** „Az átlagot pontosan két tizedesjeggyel jelenítse meg!”

**Következtetés:** a számot nem újraszámolni, hanem a kiírását formázni kell.

~~~python
atlag = 4.567
print(f"Átlag: {atlag:.2f}")
~~~

Kimenet:

~~~text
Átlag: 4.57
~~~

A `.2f` két tizedesjegyre formáz. Az eredeti változó értéke nem változik meg.

### 4.2. Vezető nullák: `03d`

**Feladatszöveg:** „A sorszám mindig legalább három számjegyből álljon, hiányzó helyeken nullával!”

~~~python
sorszam = 7
print(f"{sorszam:03d}")
~~~

Kimenet:

~~~text
007
~~~

### 4.3. Ezres csoportosítás

**Feladatszöveg:** „A nagy szám könnyebben olvasható legyen, ezres csoportokkal!”

~~~python
osszeg = 1234567

print(f"{osszeg:,}")
print(f"{osszeg:,}".replace(",", " "))
~~~

Kimenet:

~~~text
1,234,567
1 234 567
~~~

A `:,` a Python által használt vesszős ezres csoportosítást jelöli; a `replace()` itt a vesszőket szóközre cseréli a magyarosabb megjelenítéshez.

### 4.4. Százalékos megjelenítés

**Feladatszöveg:** „A 0 és 1 közötti arányt százalékban, egy tizedesjeggyel írja ki!”

~~~python
arany = 0.875
print(f"{arany:.1%}")
~~~

Kimenet:

~~~text
87.5%
~~~

Az `%` a formázás részeként megszorozza az arányt százzal, és hozzáadja a százalékjelet.

### 4.5. Előjel és tudományos jelölés

~~~python
valtozas = 12
nagy_szam = 12500

print(f"{valtozas:+d}")       # +12
print(f"{nagy_szam:.2e}")     # 1.25e+04
~~~

**Miért ezeket választjuk?** A `+d` akkor hasznos, ha a pozitív szám elé is ki kell írni a pluszjelet. A `.2e` tudományos jelölést ad két tizedesjeggyel.

### 4.6. Számformázási gyorstábla

| Elvárás | Formátum | Példakimenet |
| --- | --- | --- |
| Két tizedesjegy | `:.2f` | 4.57 |
| Háromjegyű sorszám | `:03d` | 007 |
| Ezres csoportosítás | `:,` | 1,234,567 |
| Százalék, egy tizedes | `:.1%` | 87.5% |
| Előjel is jelenjen meg | `:+d` | +12 |
| Tudományos jelölés | `:.2e` | 1.25e+04 |

**Magyar lokalizáció:** a Python alapból tizedespontot használ. Magyar tizedesvessző esetén külön alakítás vagy lokalizáció szükséges.

---

## 5. Összetett kiírás: táblázatok és riportok

### 5.1. Hogyan következtetünk a ciklusra?

**Feladatszöveg:** „Jelenítse meg a tanulók nevét, életkorát és átlagát táblázatos formában!”

Ebből a következő lépések következnek:

1. A **„tanulók”** több adatsort jelent → mindegyiket végig kell járni, ezért `for` ciklust használunk.
2. A **„táblázatos”** elrendezés fejlécet és azonos szélességű mezőket jelent → f-string.
3. A **„név, életkor, átlag”** megadja az oszlopok sorrendjét.
4. A szöveget célszerű balra, a számokat jobbra igazítani, az átlagot két tizedesjeggyel megjeleníteni.

~~~python
tanulok = [
    ["Anna", 18, 4.75],
    ["Péter", 17, 3.80],
    ["Gábor", 19, 4.20]
]

print(f"{'Név':<12}{'Kor':>6}{'Átlag':>10}")
print("-" * 28)

for tanulo in tanulok:
    print(f"{tanulo[0]:<12}{tanulo[1]:>6}{tanulo[2]:>10.2f}")
~~~

A `for` ciklus itt **nem a formázás miatt** kell, hanem azért, mert több különböző adatsort kell **ugyanazzal a formázással** megjeleníteni.

### 5.2. Keretes táblázat

**Feladatszöveg:** „A táblázatot függőleges és vízszintes vonalak határolják!”

**Következtetés:** a fejléc és az adatsorok mellett egyszerű keretkaraktereket is kiírunk.

~~~python
tanulok = [["Anna", 18], ["Péter", 17]]

print("+------------+-----+")
print(f"|{'Név':<12}|{'Kor':>5}|")
print("+------------+-----+")

for tanulo in tanulok:
    print(f"|{tanulo[0]:<12}|{tanulo[1]:>5}|")

print("+------------+-----+")
~~~

### 5.3. Különféle állapotok kiírása

**Feladatszöveg:** „Sikeres teljesítéskor MEGFELELT, egyébként NEM FELELT MEG jelenjen meg!”

**Következtetés:** a kiírt szöveg az adatoktól függ, tehát `if` feltétel szükséges.

~~~python
pont = 76

if pont >= 50:
    print("MEGFELELT")
else:
    print("NEM FELELT MEG")
~~~

### 5.4. Egyszerű ASCII-oszlopdiagram

**Feladatszöveg:** „A pontszámot minden öt pont után egy `#` karakterrel szemléltesse!”

**Következtetés:** először kiszámítjuk, hány karakter kell, majd ismétléssel kirajzoljuk.

~~~python
pont = 35
print("#" * (pont // 5))
~~~

Kimenet:

~~~text
#######
~~~

---

## 6. Haladó megjelenítések (kiegészítő tananyag)

A következő megoldások termináltól függhetnek; érettségin általában nincs szükség rájuk.

### 6.1. Színek ANSI-vezérlőkódokkal

**Feladatszöveg:** „A sikeres eredmény zöld, a hibás piros színnel jelenjen meg!”

**Következtetés:** a terminálnak színbeállító vezérlőkódokat küldünk.

~~~python
print("\033[32mSikeres művelet\033[0m")
print("\033[31mHiba történt\033[0m")
~~~

A `\033[32m` zöldet, a `\033[31m` pirosat, a `\033[0m` alaphelyzetbe állítást kér. A támogatás a termináltól függ.

### 6.2. Egy sor felülírása: `\r`

**Feladatszöveg:** „A folyamat állapota egyetlen sorban frissüljön!”

**Következtetés:** a kurzort a sor elejére irányítjuk, a következő kiírás pedig ugyanazt a sort írja felül.

~~~python
print("Állapot: 10%", end="\r")
print("Állapot: 50%", end="\r")
print("Állapot: 100%")
~~~

A `\r` kocsivissza karakter; viselkedése a termináltól függ, nem azonos a `\n` sortöréssel. A példában a gyors egymásutánban végrehajtott állapotok nem feltétlenül láthatók külön.

### 6.3. Dátumok formázása

**Feladatszöveg:** „A dátum év.hónap.nap formában jelenjen meg!”

~~~python
from datetime import datetime

datum = datetime(2026, 10, 13)
print(datum.strftime("%Y.%m.%d"))
~~~

Kimenet:

~~~text
2026.10.13
~~~

Itt a `strftime()` állítja elő a szöveges dátumot. Ez beépített Python-modul, nem külső csomag.

### 6.4. Menü kialakítása

~~~python
print("=" * 24)
print(f"{'FŐMENÜ':^24}")
print("=" * 24)
print("1. Adatok megtekintése")
print("2. Statisztika")
print("0. Kilépés")
print("=" * 24)
~~~

A menü tartalmának kiírása önmagában még nem teszi interaktívvá a programot. A tényleges választás kezeléséhez `input()` és vezérlés is kell.

---

## 7. Gyakori hibák és ellenőrzőlista

| Hiba | Miért probléma? | Hogyan javítsuk? |
| --- | --- | --- |
| `print("Név", "Kor", sep="\t")` után hosszú adatok elcsúsznak | A tabulátor nem állandó szélességű mező. | f-string mezőszélesség |
| A szöveg balra helyett jobbra igazodik | `>` szerepel `<` helyett. | `:<15` |
| A szám túl sok tizedesjegyet mutat | Hiányzik a formátum. | `:.2f` |
| A 7 helyett 007-et kérnek | Hiányzik a nulla-kitöltés. | `:03d` |
| A `print()` mindig új sort kezd | Ez az alapértelmezett `end="\n"`. | `end=" "` |
| A fejléc és az adat nem azonos oszlopban van | Eltérő szélességeket használtunk. | Azonos szélesség minden sorban |
| A szín a következő szövegre is átmegy | Nem állítottuk vissza a színt. | `\033[0m` |

**Ellenőrző kérdések kódírás előtt:**

1. Pontosan **mit** kell kiírni?
2. **Egy sorba vagy külön sorokba** kerüljenek az adatok?
3. Milyen **elválasztó** kell az értékek közé?
4. Szükséges-e **igazítás vagy mezőszélesség**?
5. Kell-e **tizedesjegy, százalék vagy vezető nulla**?
6. **Egyetlen adatot** jelenítünk meg, vagy **sok sort ciklussal**?
7. A kimenet pontosan megfelel-e a feladat **mintájának**?

---

## Kapcsolódó feladatok

A `02_gyakorlo_feladatok.md` fájl 5 szinten, összesen 40 fokozatosan nehezedő gyakorlófeladatot tartalmaz. Az első négy szint az alap- és érettségi gyakorlatra épül, az ötödik kiegészítő haladó rész.

**Tanulási javaslat:** először olvasd el a feladat szövegét, azonosítsd a kért megjelenítést, csak utána válassz Python-utasítást. A feladatok nem írják elő a kész formázási kódot, mert éppen ennek felismerését gyakoroljuk.
