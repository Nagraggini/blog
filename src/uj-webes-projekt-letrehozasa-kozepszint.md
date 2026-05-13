# Előkészületek

Gyors gombok:
A terminálból másolni ctrl+shift+c és beilleszteni a ctrl+shift+v .

Terminálban: 
cd GitHub&&mkdir webfejlesztes-modulzaro-260117-F-Andrea&&cd webfejlesztes-modulzaro-260117-F-Andrea
node -v //Ha v20 vagy v22-t látsz, akkor a következő részt hagyd ki.

Régi node esetén:
sudo apt update && sudo apt install curl
wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
source ~/.bashrc //Terminál frissítése.
nvm install --lts

Ha jó a node verziószáma, akkor ezt csináld:
npm create vite@latest .
project name: nyomj egy entert
Framework: vanilla (enter)
Variant: JavaScript (lefelé nyíl, enter)

A végén látod a localhost ip címet, amin fog futni a weboldalad, amikor az npm start-al elindítod.

File -> Open folder -> Keresd meg a projekted mappáját. 

# Mappa szerkezet

```bash
my-web-app/
├── dist/
├── src/
│   ├── assets/
│   │   ├── images/
│   │   ├── icons/
│   │   ├── fonts/
│   │   └── vendor/
│   ├── css/
│   │   ├── base/
│   │   ├── components/
│   │   ├── layouts/
│   │   └── main.css
│   ├── js/
│   │   ├── components/
│   │   ├── services/
│   │   ├── utils/
│   │   ├── config/
│   │   └── main.js
│   └── index.html
├── .github/
├── tests/
├── .gitignore
├──  index.html
├── package.json
└── README.md
```

A fenti mappa szerkezetet, így tudod profin létre hozni?
Terminal -> New Terminal

mkdir -p src/assets/{images,icons,fonts,vendor} src/css/{base,components,layouts} src/js/{components,services,utils,config} .github tests && touch src/css/main.css src/js/main.js README.md .gitignore && rm src/counter.js src/main.js src/style.css && rm src/assets/javascript.svg src/assets/vite.svg&& find src -type d -empty -not -path '*/.*' -exec touch {}/.gitkeep \;

index.html fájlba ezt írd be:
```html
<!doctype html>
<html lang="hu">
    <head>
        <meta charset="UTF-8" />
        <link rel="icon" type="image/svg+xml" href="/favicon.svg" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />

        <link rel="stylesheet" href="/src/css/main.css" />

        <title>Webfejlesztés Modulzáró - Freud Andrea</title>
    </head>
    <body>
        <div id="app"></div>

        <script type="module" src="/src/js/main.js"></script>
    </body>
</html>

```

# Feltöltés GitHub-ra

GitHub Desktop -> File -> Add local repo
-> Keresd meg a projekt mappáját. -> Add repo.

Add hozzá az első commit-od bal oldalt. 
Után publikáljuk a repot: jobb oldal Publish repo -> Publish repo


# GitHub Actions

<!--TODO -->
1. Minőségellenőrzés (CI - Continuous Integration || Continuous Integration) -> pl.: Playwright
2. Automatikus Közzététel (CD - Continuous Deployment || Deployment) -> pl.: GitHub Pages, Vercel
3. Karbantartás és Biztonság (Automation)-> 
    Dependabot: Automatikusan figyeli a package.json-t, és ha valamelyik npm csomagnak (pl. Vite) kijön egy biztonsági frissítése, nyit neked egy Pull Requestet vele.

    Lighthouse CI: Minden commit után lefut egy audit, és megmondja, mennyire lett gyorsabb vagy lassabb az oldalad (SEO, Performance, Accessibility).

## Ha nem lehet publikus a forráskód

<!--TODO-->
Privát kód esetén ez kell: Netlify, vagy Vercel, vagy Firebase Hosting kell.

### Vercel beállítása

https://vercel.com/-ra regisztrálj.

Jobb oldalt Add New ...-> Projects -> Választ ki a privát repo-t a listából Import gombbal.

Application Preset: Vite //Ha nem jól mutatná. -> Deploy -> Várj kicsit. -> Continue to Dashboard

A Domains részen láthatod a weboldalad linkjét. Jelen esetben: https://webfejlesztes-modulzaro-260117-f-an.vercel.app/

### vite.config.js vercel esetén.

Terminálba ezt másold be:

echo "import { defineConfig } from 'vite'

export default defineConfig({
  // A relatív útvonal a vercelhez.
    base: "./",
})" > vite.config.js

Ezután commitolj és mehet a push and pull a GitHub Desktop alkalmazásban.

# Linting beállítása

A linting egy automatizált ellenőrzés, amely még futtatás előtt kiszúrja a kódban a szintaktikai hibákat, a gyanús megoldásokat és a stílusbeli következetlenségeket, így segít tisztább és bugmentesebb szoftvert írni.

Fontos, hogy ne legyen deploy, vagy bármi workflow fájlod. Itt csekkold le: .github/workflows/ ÜRES!
Teriminálba:
npm install eslint --save-dev
npx eslint --init 
Megjelenik az interaktív konzolos menü. Első kérdésre yes. JS-re entert nyomj. "To check syntax and find problems"-t válaszd.
Válaszd a JavaScript modules (import/export)-ot (Vite-nál ez kell).
Válaszd a None of these-t (ha sima JS/HTML/CSS a projekt).
TypeScript: No
Browser-t válaszd.
A végén az installra yes-t nyomj. 
Az npm-et válaszd.

Ha mindent jül csináltál, akkor van egy eslint.config.js fájlod. 

Ezzel tudod lecsekkolni magad, ezt írd be a terminálba "npx eslint ." , ha nem történik semmi, akkor sikerült a konfig és telepítés. 

## Linting automatizása

package.json fájlba ezt írd be:

```json
 "scripts": {
    "dev": "vite",
    "build": "vite build",
    "preview": "vite preview",
    "lint": "eslint ."
  },
```

  Ez volt a régi:

```json
   "scripts": {
    "dev": "vite",
    "build": "vite build",
    "preview": "vite preview"  
  },
```
Futtatás terminálban: npm run lint

# Ha publikus lehet a forráskód

Nyisd meg a böngészőben a github-os repodat. -> Settings -> Lentebb görgess a legvégére. -> Change visibility -> Change to public

Aztán felül bal oldalt Pages.

Itt a "Build and deployment" résznél a forrás (Source) maradjon Deploy from a branch, a Branch-nél pedig válaszd ki a main ágat és kattints a Save gombra.

Ekkor a GitHub elindít egy folyamatot (ezt látod az Actions fülön), és 1-2 percen belül kapsz egy linket, ami így néz ki: https://felhasznalonev.github.io/repo-neve/.

## GitHub Pages beállítása (Vite + GitHub Actions)

### Első módszer

Nyisd meg a böngészőben a github-os repodat. -> Settings -> Actions -> General -> Read and write permissions -t pipáld be.

A GitHub Actions szempontjából a Vite projekt csak egy sima Node.js projekt, amit meg kell kérni, hogy futtassa le az npm run build-et.

Nyisd meg a böngészőben a github-os repodat. -> Actions -> set up a workflow yourself 
nevezd át felül deploy.yml-re. Látod mellette a master/main nevet az a branch neve.
### Második módszer

Terminálba: mkdir .github/workflows&&touch .github/workflows/deploy.yml

### Első, vagy második módszer után ez jön

Ezt másold bele: 
```yml
name: Deploy to GitHub Pages

on:
    push:
        branches: [master] # A fenti brach névvel egyeznie kell!

permissions: # Engedélyek: olvasás, írás meg a token írás, ha van.
    contents: read
    pages: write
    id-token: write

jobs:
    build-and-deploy:
        runs-on: ubuntu-latest
        steps:
            - name: Checkout
              uses: actions/checkout@v4 # Marketplace-ről: Letölti a kódot.

            - name: Set up Node
              uses: actions/setup-node@v4 # Marketplace-ről: Beállítja a Node.js-t.
              with:
                  node-version: 20
                  cache: "npm"

            - name: Install dependencies
              run: npm install

            - name: Build
              run: npm run build # Ez hozza létre a 'dist' mappát.

            - name: Setup Pages
              uses: actions/configure-pages@v4 # Beállítja a környezetet.

            - name: Upload artifact
              uses: actions/upload-pages-artifact@v3 # Feltölti az újonnan létrehozott 'dist' mappát.
              with:
                  path: "./dist"
            - name: Deploy to GitHub Pages
              id: deployment
              uses: actions/deploy-pages@v4 # Publikálja az oldalt.

```
Jobb szélen a Documentation alatt láthatod a fentiek magyarázatát. A tabulátorokra és szóközökre érzékeny a yml fájlt.

Kattints a Commit changes-re. -> Commit changes

### vite.config.js GitHub Pages esetén

Terminálba ezt másold be:

echo "import { defineConfig } from 'vite'

export default defineConfig({
  // A 'repo-neve' helyére írd be a GitHub repód pontos nevét per jelek közé!
  base: '/webfejlesztes-modulzaro-260117-F-Andrea/',
})" > vite.config.js

Ezután commitolj és mehet a push and pull a GitHub Desktop alkalmazásban.

**Későbbi teszteknél ezt használd:**
Élesítés: Terminálba: git push -> A GitHub YAML fájlja átveszi a stafétát, és 1-2 perc múlva kint van az oldalon.

# Badge-k a readme fájlba

![Workflow neve](https://github.com/Nagraggini/my-project/actions/workflows/playwright.yml/badge.svg)
![Branches](.github/badges/branches.svg)
![HTML](https://img.shields.io/badge/HTML-60%25-purple?style=flat-square&logo=java)
![License](https://img.shields.io/badge/license-MIT-green)

---------------------------------------------------------------------------------------------------------------

# Local teszthez

Fejlesztés:                 
    Terminálba ezt írd be: npm run dev -> Kódolsz, látsz minden változást élőben.       

    Leállításhoz a terminálba kattintsd beel és ctrl+c      

Ellenőrzés (opcionális):            
    npm run lint -> Megnézed, "szép-e" a kódod és nincs-e benne hiba.       

    npm run build -> Megnézed, minden rendben van-e a végleges fájlokkal. Legenerálod a dist mappát és a benne lévő index.html fájlt csekkold.      

Commitoláshoz:      
    Kijelölés: git add .            
    Mentés: git commit -m "Upload README.md"            
    Feltöltés: git push     

Csekkolás:      
    git status      