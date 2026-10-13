# Rendrakás a Varázsviccben — így kerül fel a GitHub Pages-re

Ez a mappa (`pages`) egy kész, feltölthető weboldal: maga a játék. Ugyanúgy megy, mint a
mahjongnál: egy nyilvános GitHub-tárolóba töltöd fel, és a GitHub Pages egy saját webcímen
kiszolgálja. Onnan megnyitható az Xbox Microsoft Edge böngészőjében és a számítógépen is.

A játék a Weasley Varázsvicc Vállalatban (Abszol út 93.) játszódik: zárás után a szétszóródott gyűjtői figurákat
kell a polcukra rakni.

A mappában ezek vannak:

- `index.html` – maga a játék
- `sw.js` – az offline működéshez kell (az első megnyitás után internet nélkül is indul)
- `manifest.webmanifest` és az `icons` mappa – az ikon és a telepíthető alkalmazás adatai
- `assets` mappa – a textúrák és a figurák adatai (`figures-baked`), és ha lesznek, a saját 3D-s figurák;
  ez nélkülözhetetlen, a teljes mappát töltsd fel. Az `assets/music` mappába kerülhetnek a saját zenéid
  (lásd a 7. pontot).
- `figures-preview.html` – a figurák előnézete (nem kötelező, de nem is árt)
- ez az `OLVASSEL.md` (nem kötelező feltölteni)

---

## 1. Feltöltés (egyszer, kb. 5 perc)

1. Lépj be a **github.com** oldalon (ha még nincs fiókod, készíts egyet).
2. Jobb felül **+** → **New repository**. Név például: `varazsvicc`.
   Legyen **Public** (az ingyenes Pages csak nyilvános tárolóval működik). Kattints a
   **Create repository** gombra.
3. Az üres tároló oldalán kattints az **uploading an existing file** linkre
   (vagy később: **Add file → Upload files**).
4. Nyisd meg a számítógépen a `pages` mappát, jelöld ki a **teljes tartalmát** (fájlokat és
   mappákat is: `index.html`, `sw.js`, `manifest.webmanifest`, `figures-preview.html`, `icons`,
   `assets`), és húzd be őket a böngészőablakba. Az Edge és a Chrome a mappaszerkezetet is
   megtartja.
5. Várd meg, amíg minden fájl felkerül, majd lent **Commit changes**.
6. A tároló **Settings → Pages** menüjében a **Source** legyen `Deploy from a branch`, a branch
   `main`, a mappa `/ (root)`. Kattints a **Save** gombra.
7. Egy-két perc múlva megjelenik a cím:
   `https://FELHASZNALONEVED.github.io/varazsvicc/`

A tároló nyilvános: a cím ismeretében bárki megnyithatja. Ez egy saját, magáncélú rajongói
játék, ezért a linket ne oszd meg szélesebb körben.

---

## 2. Játék az Xboxon

1. Indítsd el az Xboxon a **Microsoft Edge** böngészőt, és írd be a fenti címet
   (érdemes kedvencekhez adni, hogy legközelebb egy gombnyomás legyen).
2. Az Edge a kontrollert alapból egérmutatóként használja. **Tartsd lenyomva a Menü gombot**
   (a három vonalas gomb), és a megjelenő menüben válaszd a **játékvezérlős módot**. Ezután a
   karok és a gombok a játékot irányítják. Ugyanígy, a Menü gomb hosszú lenyomásával léphetsz ki.
3. A játékban a Menü gomb **rövid** lenyomása a Szünet.
4. Teljes képernyőhöz tartsd lenyomva a **Nézet** gombot (a két négyzetes gomb).
   Ha ezután a kontroller nem reagál, nyomd meg kétszer az **Xbox** gombot.
5. A haladást a játék az Xbox böngészőjében menti, automatikusan, kb. félpercenként és
   szüneteltetéskor.

---

## 3. Játék és telepítés a számítógépen

1. Nyisd meg a címet **Edge** vagy **Chrome** böngészőben.
2. Kontrollerrel vagy billentyűzettel és egérrel is játszható (kattints a képre, hogy az egér
   a nézelődést irányítsa).
3. **Telepítés alkalmazásként:** kattints a címsor jobb szélén megjelenő telepítés ikonra, vagy
   keresd a böngésző **⋯** (Chrome-ban **⋮**) menüjében az alkalmazásként való telepítést (Edge-ben
   az Alkalmazások pont alatt). Ezután saját ikonnal, böngészősáv nélkül indul, és az első
   megnyitás után internet nélkül is.

A számítógép és az Xbox külön-külön tárolja a haladást.

---

## 4. Frissítés

Ha új változat készül (`node build.mjs` a `game` mappában), töltsd fel újra a `pages` mappa
teljes tartalmát ugyanebbe a tárolóba (**Add file → Upload files**, a régi fájlokat felülírja),
majd **Commit changes**. A `sw.js` verziója magától változik, így a következő megnyitáskor az
új változat jön be. Ha mégis a régi látszik, töltsd újra az oldalt még egyszer.

---

## 5. Saját 3D-s figurák

Ha később egy 3D-s alkotó elkészít egy-egy figurát, a fájlokat a `game\assets\figures-src\`
mappába kell tenni, utána `node build.mjs`, és a `pages` mappát újra fel kell tölteni. A
részleteket a `game\MODEL-SPEC.md` írja le. A játék csak azokat a figurákat cseréli le, amelyekhez
van fájl; a többi marad a beépített változat.

---

## 6. A mentés

A játék a böngésző saját tárolójában ment, két váltakozó mentéshellyel, így egy félbeszakadt
mentés sem rontja el a haladást. A Szünet menüben látszik, mikor volt az utolsó mentés, és ott
van a **Mentés törlése** is (megerősítést kér). Ha törlöd a böngészőadatokat, a mentés is
elvész.

---

## 7. Saját zene

A játék a saját háttérzenéidet is lejátssza. Nem kell hozzá semmit összerakni, elég feltölteni a
fájlokat a GitHubon.

1. Nevezd el a fájlokat így: `zene-1.mp3`, `zene-2.mp3`, `zene-3.mp3` … legfeljebb `zene-20`
   (kisbetűvel, szóköz nélkül, a számozás 1-től, kihagyás nélkül). `.ogg` és `.m4a` is jó
   ugyanilyen névvel. MP3-nál 160–192 kbit/s ajánlott; egy fájl legfeljebb 25 MB lehet.
2. A tárolóban nyisd meg az `assets` mappát, majd **Add file → Upload files**. Ha még nincs
   `music` mappa, húzd be a gépeden előkészített `music` mappát a zenékkel együtt (a GitHub üres
   mappát nem tárol, ezért a mappa az első zenével együtt jön létre). Ha már van, nyisd meg az
   `assets/music` mappát, és oda töltsd fel a fájlokat. Végül **Commit changes**.
3. Egy-két perc múlva, a játék újratöltése után a saját zene lesz az alapértelmezett. A pult
   **zenélő dobozával** válthatsz: Saját zenék → Esti dallam → Gyertyafény → Csend. A hangerőt a
   Beállítások **Zene hangereje** csúszkája állítja. Az első lejátszás után internet nélkül is szól.

A tároló nyilvános, a zenéket bárki letöltheti: csak saját vagy szabad licencű (CC0, CC-BY a
szerző feltüntetésével) zenét tölts fel. A játék frissítésekor (4. pont) a zenék megmaradnak, a
feltöltés nem törli őket. Részletek: `assets/music/OLVASSEL-ZENE.txt`.
