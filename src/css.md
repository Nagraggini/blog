# CSS stílusok a weboldalakhoz

# Tartalomjegyzék
- [CSS stílusok a weboldalakhoz](#css-stílusok-a-weboldalakhoz)
- [Tartalomjegyzék](#tartalomjegyzék)
- [Forrásaim](#forrásaim)
- [Alapok](#alapok)
- [Futtatás](#futtatás)
- [F12](#f12)
- [Miért nem tölt be a js/css?](#miért-nem-tölt-be-a-jscss)
  - [Abszolut vs relatív útvonal](#abszolut-vs-relatív-útvonal)
- [Extra szelektor (Selector)](#extra-szelektor-selector)
- [Ikonok](#ikonok)
- [Media Query használata](#media-query-használata)
- [Modern CSS](#modern-css)
- [Media Query helyett if](#media-query-helyett-if)
  - [Pszeudó (pseudeo)](#pszeudó-pseudeo)
- [Régebbi böngészők](#régebbi-böngészők)
- [Tailwind telepítése:](#tailwind-telepítése)

# Forrásaim
https://www.w3schools.com/css/default.asp     
https://www.w3schools.com/htmlcss/default.asp     
[100+ Web Development Things you Should Know](https://youtu.be/erEgovG9WBs?si=vEFXO3P_WufyaR-C)     
[HTML & CSS for Absolute Beginners](https://www.youtube.com/playlist?list=PL4-IK0AVhVjOJs_UjdQeyEZ_cmEV3uJvx)     
http://www.flexboxdefense.com/      
https://flukeout.github.io/       

# Alapok

Érdemes előre megtervezni a weboldal kinézetét. Például itt: https://draw.io/
Elég egy sematikus ábra, hogy kb itt lesz ennyi gomb stb. Ezt fogja majd tudni.

A tartalmakhoz adunk stílust a css-el. Bizonyos korlátokon belül lehet némi interaktivitást is csinálni css-el pl.: egérműveleteknél, színváltoztatás. Interaktivitás fokozásához javascriptre van szükség.


Ezekkel játékosan meg lehet tanulni a CSS használatát: 
https://flexboxfroggy.com/#hu
https://cssgridgarden.com/#hu
http://www.flexboxdefense.com/           
https://flukeout.github.io/              

[Itt](https://codepen.io/) tudsz gyakorolni.
CSS magyarázatok és interaktív példákat [itt](https://www.w3schools.com/css/default.asp) találsz, valamint [itt](https://www.w3schools.com/htmlcss/default.asp).

![CSS szintaktika](/assets/CSS/css-sytax.png)

```css
body {
  background-color: lightblue;
}

h1 {
  color: white;
  text-align: center;
}

p {
  font-family: verdana;
  font-size: 20px;
}

/*Univerzális szelektor.*/
*{

}
```

Ezeket együtt érdemes használni:
```css
    display: flex;
    flex-direction: column;
    align-items: center; /*Ezt együtt kell használni pl.: flex/grid-el*/

    /*
    justify-content: "Hova tegyem az elemeket a sorban?" Jobbra balra pl
    align-items: "Hova tegyem az elemet a saját sora magasságán belül? Oszlopnál jó."
    align-content: "Hova tegyem az egymás alatt lévő sorokat?"
    */
```
**justify-content**

flex-start: group items at the start of a container's main axis
flex-end: group items at the end of the main axis
center: group items in the center of the main axis
space-between: evenly distribute items along the main axis such that the first item aligns at the start and the final item aligns at the end
space-around: evenly distribute items along the main axis such that all items have equal space around them

**align-items**

flex-start: align items across the start of a container's cross axis
flex-end: align items across the end of the cross axis
center: align items across the center of the cross axis

**Accordingly, flex-direction accepts the following values:**

row: lay out the main axis from left to right
row-reverse: lay out the main axis from right to left
column: lay out the main axis from top to bottom
column-reverse: lay out the main axis from bottom to top

**order**

The order property defines the order in which an item appears in the flex container and accepts both positive and negative integer values. All flex items begin with a default order of 0, so an item with an order greater than 0 will be repositioned relative to items still set to their default orders.

#: position an item relative to the other items in the container

**align-self**

To vertically position individual towers, use align-self, which accepts the same values as align-items.

flex-start: align item at the start of a container's cross axis
flex-end: align item at the end of the cross axis
center: align item at the center of the cross axis
Reminder: align-self, like align-items, also accepts the values baseline and stretch, but these values cannot be used in Flexbox Defense.

# Futtatás

VC Code-ban töltsd le a Live Servert. Bal oldalt az Explorerben kattints jobb klikkel az adott html fájlodra -> Open with Live Server. Rögtön elindul a böngésződben a http://127.0.0.1:5500/ -on a weboldalad.

Ctrl+F5 csodákra képes, ha épp valami nem töltene be, pedig már lekódoltad.

# F12

Futtatáskor az F12-t nyomd meg a böngészőben, válaszd a kis nyíl ikont (kijelölő), és kattints egy adott részre amit ellenőrizni szeretnél. A böngésző narancssárgával jelzi a margót (margin) és zölddel a párnázást (padding). Így pontosan látni fogod, melyik elem "tolja" el a másikat!

Felül a kis nyíl mellett van az eszköz váltó, vagyis meg tudod nézni, hogy telón hogyan néz ki. Akár fel is tudod venni a telefonodat is: Bal felül Dimension melletti nyílra katt -> Edit -> Add custom device -> Add meg a telefonod nevét és pixelben a magasságát és szélességét (Ha nem tudod kérdezd meg az AI-t.) Device pixel ratio:3 -> Save.

Application -> Storare bal oldalt -> Local storage -> Itt látod az elmentett adatokat (JS-ben localStorage-el tudsz menteni.), ha vannak.

# Miért nem tölt be a js/css?

Futtatáskor nyomd mega  böngészőben az F12-t. -> Sources -> Page -> Csekkold le, hogy ott vannak-e a css/js fájlok.

## Abszolut vs relatív útvonal

A mappa szerkezeted (példa):
Tegyük fel, hogy így néz ki a projekted:

```plaintext
my-website/
├── index.html           <-- Te itt állsz a böngészővel
├── about.html
└── components/          <-- Ez egy almapa
    └── header.html      <-- Ezt akarod betölteni
```

1. Rossz módszer (Abszolút útvonal)
const path = "/components/header.html";

Jelentése: "Menj a legelső főkapuhoz (szerver gyökér), és ott keresd a components mappát."

Hiba: Ha GitHubon a projekted a /my-website/ mappában van, a főkapunál nem lesz components mappa, csak a my-website mappán belül. Offline is elromlik, mert a számítógéped "főkapuja" a C:/ meghajtó vagy a localhost gyökere.

2. Jó módszer (Relatív útvonal)
const path = "./components/header.html";
(Vagy egyszerűen: components/header.html)

Jelentése: "Nézz körbe abban a mappában, ahol most vagyunk (./), keress egy components mappát, és menj bele."

Miért jó? Mindegy, hogy a mappád neve my-website vagy valami-mas, és mindegy, hogy a GitHubon van vagy a gépeden. Mivel az index.html mellett ott van a components mappa, mindig meg fogja találni.

Kipróbálható kódpélda
Ha az index.html fájlból futtatod a scriptet, így nézzen ki a fetch:

```JavaScript
// A lényeg: NINCS perjel az elején!
const url = "components/header-component.html"; 

async function loadHeader() {
    try {
        const response = await fetch(url);
        if (response.ok) {
            const html = await response.text();
            document.getElementById("header-helye").innerHTML = html;
        } else {
            console.error("Nem találom a fájlt ezen az úton:", url);
        }
    } catch (hiba) {
        console.error("Hiba történt:", hiba);
    }
}

loadHeader();
```

# Extra szelektor (Selector)

html

```html
<h2>Continents 🗺️</h2>
<ul>
  <li>Africa</li>
  <li>Antarctica</li>
  <li>Asia</li>
  <li>Australia</li>
  <li>Europe</li>
  <li>North America</li>
  <li>South America</li>
</ul>

<h2>Oceans By Size 🌊</h2>
<ol>
  <li>Pacific</li>
  <li>Atlantic</li>
  <li>Indian</li>
  <li>Antarctic/Southern</li>
  <li>Arctic</li>
</ol>
```
css
```css
ul > li { 
    /* Csak azokra az elemekre érvényes, amelyek közvetlenül az ul alatt vannak, nem mélyebben, vagyis jeleneseben, csak az elsőre.   */
  border: 1px solid;
  width: 50px;
}
```

[Ez](https://specifishity.com/specifishity.pdf) az egyik legjobb magyarázat a css szelektorokra.

# Ikonok

https://fonts.google.com/icons

# Media Query használata

Fontos, hogy a html tagjében ez szerepeljen, ezzel érzékelni fogja, hogy épp mobilon vagy asztali böngészőben nézi a felhasználó az oldalt:
```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```
A css-ben:
```css
@media (max-width: 768px) {
    /* Ide jönnek a mobilra szánt módosítások */
}
```

# Modern CSS

# Media Query helyett if

https://www.youtube.com/watch?v=THvg9DQPs94&list=WL&index=18

max-width:767px

max-width: 1024px


## Pszeudó (pseudeo)

Modern verzió a pszeudóra:
1. ::before és ::after

Többit [itt](https://www.codedex.io/css/bonus/pseudo-elements-in-css) találod. 

Modern 

```css
/*A :has() segítségével megváltoztathatod egy eleme stílusát attól függően, hogy mi van benne. De ez, csak akkor működik, ha nem a js-ben van a módosítás. :( */
h2:has(.Andi) {
    background-color: rgba(255, 255, 255, 0.716);
    color: white;
}
```

---

# Régebbi böngészők

Sok régi böngésző nem támogatja a modern css-t. Emiatt érdemes a css-auto-prefix vs code kiegészítőt letölteni.

# Tailwind telepítése: 

Terminálban: 

//Ellenőrizd Node.js és npm verziót. node 16+ az ajánlott.
node -v
npm -v

//Ha nincs, akkor.
npm install

//Projekt gyökerében hozd létre a package.json-t (ha még nincs)
npm init -y

//Telepítsd Tailwind-et fejlesztői függőségként
npm install -D tailwindcss@3

//Ha már van telepítve, vagy problémák vannak, érdemes törölni a node_modules-t és a lock fájlt:
rm -rf node_modules package-lock.json
npm install

//Tailwind konfiguráció létrehozása. Ez létrehozza a tailwind.config.js fájlt.
npx tailwindcss init

//Ha akarod, a -p kapcsolóval rögtön létrehozza a PostCSS configot is:
npx tailwindcss init -p

CSS fájl elkészítése

CSS:
A src/main/resources/static/css/input.css legyen így:
@tailwind base;
@tailwind components;
@tailwind utilities;

HTML:
<link rel="stylesheet" href="/css/output.css">

Le kell buildelni a css fájlt:
npx tailwindcss -i ./src/main/resources/static/css/input.css -o ./src/main/resources/static/css/output.css --watch

---
