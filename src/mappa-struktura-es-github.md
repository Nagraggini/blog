Webes projekt mappa struktúrája ilyen legyen:

```bash
projekt-neve/
├── index.html                  # A fooldal (belepesi pont)
├── pages/                      # Aloldalak
│   ├── contact-us.html
│   └── about-me.html
├── assets/                     # Statikus eroforrasok
│   ├── css/
│   │   ├── main-style.css
│   │   └── header-style.css
│   ├── js/
│   │   ├── load-components.js
│   │   └── theme-switch.js
│   ├── images/
│   │   └── hero-banner.jpg
│   ├── fonts/
│   │   └── roboto-regular.woff2
│   └── icons/
│       └── favorite-icon.svg
├── components/                 # Ujrafelhasznalhato HTML reszletek
│   ├── header-component.html
│   ├── footer-component.html
│   └── sidebar-navigation.html
├── docs/                       # Dokumentacio es segedanyagok
│   ├── syllabus/               # Tananyagok (pl. istqb-syllabus-hu.pdf)
│   ├── architecture-plan.md    # A projekt felepitesenek leirasa
│   └── guides/
│       └── testing-guide.md    # Utmutatok a teszteleshez
├── tests/                      # Tesztelesi mappa (Playwright/E2E)
│   ├── e2e/                    # End-to-end tesztek
│   │   └── user-login.spec.js
│   ├── components/             # Komponens-szintu tesztek
│   │   └── header-check.spec.js
│   ├── fixtures/               # Tesztadatok
│   │   └── test-users.json
│   └── utils/                  # Segedfuggvenyek
│       └── test-helpers.js
├── playwright.config.js        # Playwright konfiguracio
├── package.json                # Fuggosegek es scriptek
└── README.md                   # Fo leiras a projektirol
```

Mindegyik fájl ékezet nélküli és kötöjeles (Kebab-case) legyen, valamint átlátható és konzistens.

# Github branch

A Settingben állj át az új branchre és a Pages-en is.

Pages -> build and deployment -> source -> GitHub Actions -> Static HTML
A branch névre figyelj, hogy megfelelő legyen beállítva.

# Commit

Verzió követés beállítása: `git init

Új ág létrehozása: `git branch uj-branch-neve
Ágak közti váltás: `git switch branch-neve

Új branch létrehozása és azonnali átváltás: `git switch -c uj-branch-neve

Új feladat megkezdésekor érdemes külön branchet létrehozni!

**Commitolni, így kell terminálból:**
Kijelölés: `git add .
Mentés: `git commit -m "fix: "
Feltöltés: `git push

Csekkolás: `git status

Hogyan épül fel egy profi commit üzenet? (A szabály)
A Conventional Commits szabvány szerint az üzenet így néz ki: <típus>: <rövid leírás jelen időben>

A legfontosabb típusok (types), amiket egy tesztautomatizálónak ismernie kell:

- ci: Minden, ami a GitHub Actions-re, pipeline-okra, Dockerre vagy futtató környezetekre vonatkozik. 
- feat: Új funkció (pl. új tesztosztály írása, új Page Object létrehozása).
- fix: Hibajavítás (pl. egy elbukó teszt javítása, rossz lokátor korrigálása, NullPointerException javítása).
- refactor: Kód szépítése, átírása anélkül, hogy a működés változna (pl. a Page Chaining bevezetése a meglévő tesztek alá).
- test: Tesztek hozzáadása vagy módosítása (ha nem az architektúra, hanem konkrétan a teszteset változik).
- chore: Apróbb karbantartások, amik nem módosítanak forráskódot (pl. .gitignore frissítése, verziószám emelése a pom.xml-ben).

💡 Aranybölcsességek a commitokhoz:
Írd jelen időben és felszólító módban (angolul): Ne azt írd, hogy fixed url bug, hanem hogy fix url bug. (Úgy gondolj rá, 
mintha a commit egy utasítás lenne a Git-nek: "Ha ezt a commitot alkalmazod, az meg fogja javítani az URL bugot.")

Kis kezdőbetű: A kettőspont utáni leírást kisbetűvel kezdjük, és a végére nem teszünk pontot.

Fokozatosság: Ne egyszerre küldd be a CI-t, a refaktorálást és a javításokat! Érdemesebb 3-4 kisebb commitot csinálni egymás után, mert ha valami elromlik, sokkal könnyebb lesz visszagörgetni a kódot.