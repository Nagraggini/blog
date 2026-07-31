# Tartalomjegyzék


- [Tartalomjegyzék](#tartalomjegyzék)
- [Playwright](#playwright)
- [Telepítés](#telepítés)
  - [Projekt létrehozása + workflow nélkül](#projekt-létrehozása--workflow-nélkül)
    - [Workflow](#workflow)
- [Saját weboldal tesztelése](#saját-weboldal-tesztelése)
  - [playwright.config.js](#playwrightconfigjs)
  - [package.json](#packagejson)
- [Első teszt felvételéhez](#első-teszt-felvételéhez)
- [Futtatás](#futtatás)
- [Jelszó beállítása környezeti változóként](#jelszó-beállítása-környezeti-változóként)
  - [Minta](#minta)
- [Lokátorok](#lokátorok)
- [1. Felhasználó-központú lokátorok (Ajánlott kezdetnek!)](#1-felhasználó-központú-lokátorok-ajánlott-kezdetnek)
    - [`getByText()`](#getbytext)
    - [`getByRole()`](#getbyrole)
    - [`getByLabel()`](#getbylabel)
    - [`getByPlaceholder()`](#getbyplaceholder)
- [2. Hagyományos lokátorok](#2-hagyományos-lokátorok)
  - [CSS Selector](#css-selector)
    - [XPath](#xpath)
    - [Abszolút XPath](#abszolút-xpath)
    - [Relatív XPath](#relatív-xpath)
    - [XPath Tengelyek (Axes)](#xpath-tengelyek-axes)
  - [3. A lokátorok szűkítése és láncolása (Chaining \& Filtering)](#3-a-lokátorok-szűkítése-és-láncolása-chaining--filtering)
    - [Alapvető láncolás (Chaining)](#alapvető-láncolás-chaining)
    - [Lista elemeinek kiválasztása index alapján](#lista-elemeinek-kiválasztása-index-alapján)
      - [`.first()`](#first)
      - [`.last()`](#last)
      - [`.nth(index)`](#nthindex)
    - [Haladó szűrés: `.filter()`](#haladó-szűrés-filter)
      - [Szűrés szöveg alapján (`hasText`)](#szűrés-szöveg-alapján-hastext)
      - [Szűrés belső elem alapján (`has`)](#szűrés-belső-elem-alapján-has)
- [4. Példa a gyakorlatban (Kódminta)](#4-példa-a-gyakorlatban-kódminta)
- [Billentyűzet események](#billentyűzet-események)
- [Egér események](#egér-események)
- [Oldalváltás](#oldalváltás)
- [Canvas](#canvas)
- [POM](#pom)
- [Page Chaining](#page-chaining)
- [Report feltöltésének automatizálása Azure DevOps-al](#report-feltöltésének-automatizálása-azure-devops-al)


# Playwright


**Mi az a Playwright?**


Playwright egy nyílt forráskódú (open-source) eszköz, amely:


- automatizálja a webes alkalmazások tesztelését,
- támogatja a több böngészőt (Chromium, Firefox, WebKit),
- több nyelven is használható: JavaScript, TypeScript, Python, Java, C#.


Fő előnye a Seleniumhoz képest:
Gyorsabb, stabilabb és könnyebb párhuzamosan futtatni a teszteket.


# Telepítés


[Visual Studio Code](https://code.visualstudio.com/)
[Playwright Test for VSCode](https://marketplace.visualstudio.com/items?itemName=ms-playwright.playwright)


[Node.js](https://nodejs.org/en)
[Git](https://git-scm.com/install/)
[Verziókezelő program - Git Fork](https://git-fork.com/)


Engedélyezni kell, hogy a rendszer ne tiltsa le a szkriptek futtatását ezzel:
Powershellben rendszergazdaként: Set-ExecutionPolicy RemoteSigned -Scope CurrentUser


Terminálba:
npx playwright install


Ellenőrzés terminálban:
node -v
npm -v


Ha kiírja mindkettő után a verzió számokat, akkor sikeres volt a telepítés.


## Projekt létrehozása + workflow nélkül


Lépj bele a terminálban a mappába ahova a tesztet szeretnéd.


A mappa egyben a projekt neve lesz. pl.: for-test
A verzió követést, úgy tudod beállítani, hogy beírod a terminálba, miután beléptél a mappába,hogy "git init".


Playwright projekt létrehozása:
Terminálba: npm init playwright@latest


A zárójelben lévőket válaszold a terminál kérdéseire.
Do you want to use TypeScript or JavaScript? Typescript (enter),
Where to put your end-to-end tests? Marad a test mappa az alap értelmezett (tab és enter). Fontos, hogy csak egy test mappád legyen.
Add a GitHub Actions workflow? (n) // Ha szeretéd, hogy automatikusan lefussanak a tesztek, amikor commitolsz, akkor y-t válaszd.
Install Playwright browsers? (y)


Példa:
https://github.com/Streptopelia-risoria/restful_booker_platform_demo


Ha nyilvános projekt, akkor ezt érdemes beállítani:
https://app.codacy.com/ -n adjuk hozzá a repot, hogy elemezze a kódot, amit írunk. Figyelmeztet és kb tutorként segít, hogy ne legyen spagetti kód.

### Workflow

Ha kéne workflow, hogy a GitHub Actions automatikusan elindítsa a teszteket, amikor commitolsz, akkor a lentieket állítsd be.

**GitHub Actions**

Ennek meg kell lennie:
.github/workflows/playwright.yml

A szóközöre és tabokra nagyon figyelj.

```yml
name: Playwright Tests
on:
  push:
    branches: [ main, master ] # Ha más a branch neve, akkor írd át.
  pull_request:
    branches: [ main, master ] # Ha más a branch neve, akkor írd át.
jobs:
  test:
    timeout-minutes: 60
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v4
    - uses: actions/setup-node@v4
      with:
        node-version: lts/*
    - name: Install dependencies
      run: npm ci
    - name: Install Playwright Browsers
      run: npx playwright install --with-deps
    - name: Run Playwright tests
      run: npx playwright test
    - uses: actions/upload-artifact@v4
      if: ${{ !cancelled() }}
      with:
        name: playwright-report
        path: playwright-report/
        retention-days: 30
```

Ez az útmutató, hogy mi alapján futtassa a GitHub a teszteket. 

Amikor a terminálban telepítetted a playwright-ot (npm init playwright@latest), akkor yes-t kellett nyomni a GitHub Action-s kérdésre, de a fenti workflow-al ezt tudod bepótolni.

A workflow eredményét, hogy passed/failed megtudod jeleníteni a README-dben. Felülre ezt másold be és persze írd át a felhasználónevet és a reponevét.
```bash
![Workflow neve](https://github.com/FELHASZNALONEV/REPO_NEVE/actions/workflows/playwright.yml/badge.svg)
```

# Saját weboldal tesztelése

A lenti beállításokat, akkor kell megcsinálnod, ha a saját weboldaladat hostolod és azt akarod tesztelni.

## playwright.config.js

A GitHub Actions egy üres szerveren fut, ahol nincs elindítva a Live Server, ezért a playwright.config.js fájlba a lentit írd bele, amivel megmondjuk a Playwright-nak, hogy indítsa el a webszervert a tesztek előtt.

```javascript
export default defineConfig({

    use: { //Fontos, hogy ne duplikáld a use részt!
     //... korábbi sorok
        baseURL: "http://127.0.0.1:8080", // Így nem kell mindig beírni.
        actionTimeout: 10000, // 10 másodperc minden kattintásra/gépelésre
        navigationTimeout: 15000,

    // ... többi sorok
        trace: "on-first-retry",
    },

//... korábbi sorok
    /* Run your local dev server before starting the tests */
    webServer: {
        command: "npm run start",
        url: "http://127.0.0.1:8080",
        reuseExistingServer: !process.env.CI,
        stdout: 'ignore',
        stderr: 'pipe',
    },
// ... többi sor
});
```
A "projects: [..]" részen kommenteld ki a safarit és a firefox-ot, ha nem akarod a gépedre is telepíteni azokat.

## package.json

A gyökér könyvtárban lévő package.json-t ki kell egészíteni a playwright függőséggel:
```js
{
{
  }
 //... korábbi sorok 
  ,
  "devDependencies": {
    "@playwright/test": "^1.44.0"
  }
// ... többi sor
}
```

Valamint ennél:
```js
  "scripts": {},
```

Javítsd ki erre:
```js
"scripts": {
  "test": "npx playwright test",
  "start": "servor . 8080 --reload" 
} //Duplikálni nem szabad.
```

Fontos , hogy a port számnak mindenhol egyeznie kell.

Terminálba: npm install --save-dev servor

Ezek után még csekkold le, hogy tuti nem a live servert akarja használni playwright.
Terminálba írd be ezt: npx playwright test

Ha hiba van írd be ezt: npx playwright show-report
Meg tudod nézni részletesen a hibát.

Ezután jöhet a commitolás a master/main-be. "Add GitHub Actions workflow" címmel.

Ezután a GitHub-on az adott reponál az Actions lapfülön láthatod, hogy sikerült-e a teszt.

**Teljes teszthez**

Terminálban: 
Ezzel csak a chromium típusú böngészőben futtatod a tesztet.
npx playwright test --project=chromium

npm run start

Miután elindult minden a leállításhoz a terminálban nyomd meg a ctrl+C-t.
npx playwright test

Többi hasznos terminál parancs a teszteléshez:
npx playwright test --ui
npx playwright test --debug

# Első teszt felvételéhez


Bal oldalt válaszd ki a lombik ikont.


TOOLS (Eszközök)

Pick locator: Ez a legpraktikusabb. Kattints rá, menj át a böngészőbe, és mutass rá az egérrel egy elemre (pl. a gombra vagy combo boxra). A VS Code-ban azonnal megjelenik a kód, amivel az adott elemet eléred.         
Record new: Elindít egy üres tesztet és egy böngészőt. Amit a böngészőben csinálsz, azt élőben kódként rögzíti egy új fájlba. Látni fogod, hogy az Inspector ablakban automatikusan generálódik a kód.    
Ha végeztél, csak zárd be a böngészőt, és a VS Code-ban ott lesz az új tesztfájl a kész kóddal!
Bal oldalt frissítsd a test explorert és nyisd le a test részt ott láthatod az imént felvitt tesztedet. 

Record at cursor: Ugyanaz, mint az előző, de nem új fájlt nyit, hanem a meglévő kódodba, a kurzor pozíciójához szúrja be az új lépéseket.   


A fájlnevének mindig , így kell kinéznie: valami.spec.ts


Terminálba: npx playwright codegen


# Futtatás


Bal oldalt lombik ikon, aztán Play vagy Debug Test.


Vagy


Utána megjelenik a report automatikusan:
npx playwright test


npx playwright test --ui
npx playwright test --debug
npx playwright test --project=galaxy-tab --headed

Pl.: galaxy-tab -on, csak akkor tudsz tesztelni, ha be van állítva az eszköz a playwright.config.ts fájlban.


Ezzel csak a chromium típusú böngészőben futtatod a tesztet.
npx playwright test --project=chromium

# Jelszó beállítása környezeti változóként


.env fájlbe írd be e felhasználónevet és jelszót.


A gitignore-ba meg, hogy ".env" be kell írni, hogy ezt nem kell verziókezelés alávonni. A package.json mellé rakd.


Gitignore fájl tartalma:


```.gitignore
# Playwright
node_modules/
/test-results/
/playwright-report/
/blob-report/
/playwright/.cache/
/playwright/.auth/
.env
```


Terminálba:
npm install dotenv --save-dev


## Minta


```ts
import { test, expect } from "@playwright/test";
import * as dotenv from "dotenv";
dotenv.config(); // Betölti a .env fájl tartalmát


test("Google.hu", async ({ browser }) => {
  const context = await browser.newContext({
    httpCredentials: {
      username: process.env.SITE_USER || "", // A .env-ből olvassa
      password: process.env.SITE_PASS || "", // A .env-ből olvassa
    },
  });
  const page = await context.newPage();
  await page.goto("google.hu");
});
```


# Lokátorok


A Playwright lokátorok (locators) olyan objektumok, amelyek megmondják a Playwrightnak, hogy pontosan melyik HTML elemmel (gomb, beviteli mező, szöveg stb.) szeretne interakcióba lépni a weboldalon.


A Playwright lokátorok egyik legnagyobb előnye, hogy automatikusan bevárják (auto-wait) az elemet. Ez azt jelenti, hogy a Playwright ellenőrzi, hogy az elem látható és kattintható-e, mielőtt bármit is csinálna vele.


Íme a legfontosabb lokátortípusok és azok magyarázata a könnyebb megértéshez.


Stabilitási sorrend: id > cssSelector > xpath


---


# 1. Felhasználó-központú lokátorok (Ajánlott kezdetnek!)


A Playwright arra ösztönöz, hogy úgy keressünk elemeket, ahogyan egy ember látja azokat a képernyőn, nem pedig bonyolult technikai leírások alapján.


### `getByText()`


Szöveg alapján keresi az elemeket a képernyőn.


- **Példa:** `await page.getByText('Bejelentkezés')`


### `getByRole()`


Szerepkör (gomb, jelölőnégyzet, űrlap, fejléc) és a hozzá tartozó felirat alapján keres. Ez a legbiztonságosabb és leginkább hozzáférhető (accessibility) módszer.


- **Példa:** `await page.getByRole('button', { name: 'Mentés' })`


### `getByLabel()`


Címke (label) alapján keres beviteli mezőket.


- **Példa:** `await page.getByLabel('Jelszó')`


### `getByPlaceholder()`


A beviteli mezőkben halványan látható, kitöltést segítő szöveg alapján keres.


- **Példa:** `await page.getByPlaceholder('Email cím')`


---


# 2. Hagyományos lokátorok


Ha a fenti, felhasználó-központú módszerekkel nem boldogulunk (pl. mert az elemnek nincs felirata), használhatjuk a webfejlesztésben megszokott hagyományos módszereket.


## CSS Selector


Szelekciós nyelvet alkalmazó lokátorok. A `page.locator('css-szelektor')` metódussal használjuk (osztálynév `.`, vagy azonosító `#`). Ha egy elemnek több osztálya van és a HTML-ben szóköz választja el őket, a szelektorban pontot kell tenni a szóközök helyére (pl. `class="btn primary"` -> `.btn.primary`).


- **Példa:** `await page.locator('.high-light-text')`


Ugyanazt a nyelvet használja, mint a CSS az elemek formázására:


- `#` $\rightarrow$ ID alapján
- `.` $\rightarrow$ osztály (class) alapján
- `[attribútum='érték']` $\rightarrow$ attribútum alapján
- `tag.class` $\rightarrow$ tag + osztály kombinációja
- `<szóköz>` $\rightarrow$ leszármazott (bármilyen mélységben)
- `>` $\rightarrow$ közvetlen leszármazott (gyermek elem)
- `*='<érték>'` $\rightarrow$ attribútumot tartalmazza (részleges egyezés)
- `^=` $\rightarrow$ az attribútum értéke ezzel kezdődik
- `$=` $\rightarrow$ az attribútum értéke ezzel végződik


**Hátránya:** Nem tud a DOM struktúrában visszafelé (felfelé, a szülő irányába) l


### XPath

### Abszolút XPath 

Egyetlen / -el kezdődik.

*Működése:* A dokumentum legfelső gyökerétől (a gyökérelemtől) indul, és pontosan leköveti a teljes hierarchikus utat a célelemig.

*Hátránya:* Nagyon törékeny. Ha a HTML/XML struktúrában bárhol beszúrnak vagy eltávolítanak egy köztes elemet (pl. egy új `<div>`-et), a teljes útvonal érvénytelen lesz, és a teszt vagy lekérdezés elromlik.

### Relatív XPath

A `page.locator('xpath=//...')` vagy egyszerűen `page.locator('//...')` kifejezésekkel használjuk. Ezt akkor érdemes alkalmazni, ha egyedi logikára van szükség, de a bonyolultsága miatt érdemes kerülni, ha van egyszerűbb megoldás.


- **Példa:** `await page.locator('//button[@id="submit-btn"]')`


Útvonal alapú lekérdező nyelv, segítségével a DOM-ban adhatunk meg logikai útvonalat a HTML hierarchikus szerkezetét kihasználva. A dokumentum bármely pontján képes keresni az elemet, függetlenül attól, hogy az hol helyezkedik a DOM fában. Közvetlenül megcélozhatjuk a keresett elemet attribútumok (pl. `id`, `class`) vagy szöveg alapján.

- **Erőssége:** Ha nincs egyedi azonosító, akkor is stabil útvonalat biztosít az elemek egymáshoz képesti kapcsolatain keresztül.
- Képes a dokumentum struktúrájában minden irányban mozogni (felfelé és lefelé is).


**Kulcsjelei:**


- `/` $\rightarrow$ közvetlen útvonal (gyermek)
- `//` $\rightarrow$ bárhol a dokumentumban (leszármazott)
- `@` $\rightarrow$ attribútum jelölése
- `[]` $\rightarrow$ feltételek, szűrések helye
- `.` $\rightarrow$ aktuális elem
- `..` $\rightarrow$ szülő elem
- `*` $\rightarrow$ bármely elem (wildcard)
- `text()` $\rightarrow$ csak a közvetlen szöveges tartalom. (Van, amikor a `.` jobb, mert az a teljes elem beágyazott szövegeire is keres).
- `contains()` $\rightarrow$ részleges egyezés vizsgálata
- `=` $\rightarrow$ pontos egyezés vizsgálata
- `starts-with()` $\rightarrow$ az érték valamilyen szöveggel kezdődik
- _Megjegyzés:_ Az `ends-with()` az XPath 2.0+ része, a böngészők által használt


### XPath Tengelyek (Axes)


| Tengely (Axis)        | Jelentés                      | Mire jó?                                  |
| :-------------------- | :---------------------------- | :---------------------------------------- |
| `parent::`            | szülő elem                    | egy szintet feljebb lép                   |
| `ancestor::`          | bármely ős elem               | pl.: egy nagyobb blokk keresése           |
| `child::`             | közvetlen leszármazott        | Lefelé történő navigáció egy szinttel     |
| `descendant::`        | bármely mélységű leszármazott | Lefelé történő bármely mélységű navigáció |
| `following-sibling::` | következő testvér elem        | formok                                    |
| `preceding-sibling::` | előző testvér elem            | formok                                    |


---


## 3. A lokátorok szűkítése és láncolása (Chaining & Filtering)


Gyakran előfordul, hogy egy weboldal több azonos tulajdonságú elemet is tartalmaz (például egy lista elemei vagy egy táblázat sorai). Ilyenkor a lokátorokat tovább lehet szűkíteni a megfelelő metódusok egymás után fűzésével.


### Alapvető láncolás (Chaining)


A lokátorokat egyszerűen egymás után kötheted, így a Playwright a második elemet már csak az első elemen **belül** fogja keresni.


- **Példa:** `await page.locator('#nav-bar').getByRole('button', { name: 'Kijelentkezés' }).click();`


### Lista elemeinek kiválasztása index alapján


#### `.first()`


Csak a találati lista legelső elemét választja ki.


- **Példa:** `await page.locator('.product-item').first().click();`


#### `.last()`


Csak a találati lista legutolsó elemét választja ki.


- **Példa:** `await page.locator('.product-item').last().click();`


#### `.nth(index)`


Sorszám alapján választja ki az elemet. **Fontos:** A számozás 0-tól indul, így a `.nth(0)` az első elemet, a `.nth(1)` a másodikat jelenti.


- **Példa:** `await page.locator('.product-item').nth(2).click();` _(A 3. termékre kattint)_


### Haladó szűrés: `.filter()`


A `.filter()` metódus segítségével egy meglévő lokátor-listát szűkíthetsz tovább a belső tulajdonságaik alapján.


#### Szűrés szöveg alapján (`hasText`)


Csak azokat az elemeket tartja meg, amelyek (vagy amelyek gyermekelemei) tartalmazzák a megadott szöveget.


- **Példa:** `await page.locator('.row').filter({ hasText: 'Aktív' }).click();`


#### Szűrés belső elem alapján (`has`)


Csak azokat az elemeket tartja meg, amelyek belsejében megtalálható egy másik, megadott lokátor (pl. egy gomb, ikon vagy jelölőnégyzet).


- **Példa:** `await page.locator('.card').filter({ has: page.getByRole('button', { name: 'Törlés' }) }).click();` _(Csak azt a kártyát választja ki, amin van Törlés gomb)_


# 4. Példa a gyakorlatban (Kódminta)


Így néz ki a lokátorok használata a tesztkódban, beágyazva a megfelelő műveletekkel:


```ts
javascriptimport { test, expect } from '@playwright/test';


test("Lokátorok használata", async ({ page }) => {
  await page.goto("https://pelda-oldal.hu");


  // 1. Kattintás a 'Regisztráció' szöveget tartalmazó linkre/gombra
  await page.getByText("Regisztráció").click();


  // 2. Beviteli mező kitöltése a placeholder alapján
  await page.getByPlaceholder("Felhasználónév").fill("Almafa12");


  // 3. Kattintás a 'Mentés' feliratú gombra
  await page.getByRole("button", { name: "Mentés" }).click();


  // 4. Ellenőrzés: A sikeres üzenet látható-e
  await expect(page.locator(".success-message")).toHaveText("Sikeres mentés!");
});
```


# Billentyűzet események


```ts
import { test, expect } from "@playwright/test";


test("Billentyűzet események és kombinációk tesztelése", async ({ page }) => {
  // 1. Oldal betöltése és fókuszálás egy beviteli mezőre
  await page.goto("https://example.com");
  const input = page.locator("#username");
  await input.focus();


  // 2. Egyszerű gombnyomás (Alfanumerikus gombok)
  await page.keyboard.press("a");
  await page.keyboard.press("1");


  // 3. Navigációs és Szerkesztő billentyűk
  await page.keyboard.press("Tab"); // Fókusz a következő elemre
  await page.keyboard.press("Backspace"); // Utolsó karakter törlése
  await page.keyboard.press("Enter"); // Űrlap elküldése / Nyugtázás
  await page.keyboard.press("Escape"); // Modális ablak bezárása


  // 4. Nyíl billentyűk (Pl. legördülő menükhöz vagy egyéni komponensekhez)
  await page.keyboard.press("ArrowDown");
  await page.keyboard.press("ArrowUp");


  // 5. Oldalnavigáció
  await page.keyboard.press("PageDown"); // Görgetés lefelé
  await page.keyboard.press("End"); // Oldal legaljára ugrás


  // 6. Módosító billentyűk és kombinációk (Ctrl + A, majd Ctrl + C)
  // macOS esetén a "Control" helyett a "Meta" (Command) billentyűt kell használni
  const modifier = process.platform === "darwin" ? "Meta" : "Control";


  await page.keyboard.down(modifier); // Lenyomva tartás
  await page.keyboard.press("a"); // Mindent kijelöl
  await page.keyboard.press("c"); // Másolás vágólapra
  await page.keyboard.up(modifier); // Felengedés


  // 7. Kombináció egyetlen lépésben (Rövidített Playwright szintaxis)
  // A Playwright támogatja a gombok plusszjellel (+) való összefűzését is
  await page.keyboard.press(`${modifier}+v`); // Beillesztés vágólapról


  // Shift+Tab példa (visszafelé navigálás)
  await page.keyboard.press("Shift+Tab");
});
```


# Egér események


```ts
import { test, expect } from "@playwright/test";


test("Egér események tesztelése", async ({ page }) => {
  await page.goto("https://example.com");
  const gomb = page.locator("#submit-btn");


  // 1. Alapvető kattintások (Locator alapon)
  await gomb.click(); // Sima bal klikk
  await gomb.dblclick(); // Dupla kattintás
  await gomb.click({ button: "right" }); // Jobb klikk (helyi menü)
  await gomb.click({ button: "middle" }); // Középső klikk (görgő)


  // 2. Billentyűvel kombinált kattintások
  await gomb.click({ modifiers: ["Control"] }); // Ctrl + Klikk (kijelöléshez)
  await gomb.click({ modifiers: ["Shift"] }); // Shift + Klikk


  // 3. Egér rámutatás (Hover) és elmozdítás
  await gomb.hover(); // Ráviszi az egeret (pl. lenyíló menükhöz)


  // 4. Vonszolás (Drag and Drop) - Egyszerű verzió
  // Forrás elem elhúzása a célelemre
  await page.locator("#source-item").dragTo(page.locator("#target-zone"));


  // 5. Precíz egérmozgások koordinátákkal (page.mouse)
  // Az egér mozgatása a képernyő egy adott X, Y pontjára
  await page.mouse.move(100, 200);


  // Manuális vonszolás koordinátákkal (Klikk -> Mozgatás -> Felengedés)
  await page.mouse.down(); // Bal egérgomb lenyomása és nyomva tartása
  await page.mouse.move(300, 400, { steps: 10 }); // Elmozdítás 10 lépésben (folyamatosabb)
  await page.mouse.up(); // Egérgomb felengedése


  // 6. Egérgörgő használata (Görgetés / Wheel)
  // deltaX: vízszintes, deltaY: függőleges görgetés képpontban (pixel)
  await page.mouse.wheel(0, 500); // 500 pixelt görget lefelé
});
```


# Oldalváltás


```ts
// Váltás/Interakció: Egyszerűen az adott változót használod
// Visszavált az első fülre (előtérbe hozza)
await page.bringToFront();
```


# Canvas


```ts
// Térképre történő kattintás.
await page.locator("canvas.ol-fixedoverlay").click({
  position: {
    x: 400,
    y: 180,
  },
});
```


# POM

A POM az automata tesztelésben a Page Object Model (Oldalobjektum-modell) rövidítése. Ez a legnépszerűbb és legelterjedtebb tervezési minta (design pattern) a UI-tesztelésben (Playwright, Selenium, Cypress).

Lényege, hogy a weboldal egyes oldalait (vagy nagyobb komponenseit, pl. fejléc, menü) külön JavaScript/TypeScript osztályokként (Class) modellezzük le.

# Page Chaining

A Page Chaining egy tervezési minta, amelyet általában a Page Object Model (POM) mellett használunk Playwright teszteknél.

A lényege:

Egy oldalon végrehajtott művelet után a metódus visszaadja a következő oldal objektumát, így a teszt folytatható a következő oldalon.

A teszt folyamatot oldalról oldalra lehet vezetni:

LoginPage
     ↓
DashboardPage
     ↓
ProfilePage

Ha nincsen oldalváltó művelet, akkor az adott oldal objektumát adja vissza. 

# Report feltöltésének automatizálása Azure DevOps-al

Statikus html oldalként fog megjelenni.

Útmutatók a beállításához:
https://ultimateqa.com/playwright-reporters-how-to-integrate-with-azure-devops-pipelines/

https://bogdanbujdea.dev/publishing-playwright-report-as-an-artifact-in-azure-devops?source=more_series_bottom_blogs



