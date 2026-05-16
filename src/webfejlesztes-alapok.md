# Visual Studio Code

Egy népszerű, ingyenes kódszerkesztő, amelyhez rengeteg bővítmény érhető el.

Innen tudod letölteni. https://code.visualstudio.com/
Miután letöltötted, telepítetted és megnyitottad. File -> New Text File ezután katt a “select a language”-re és válaszd ki ami kell épp.

## VS Code beállítása

Format On Save-t pipáld be.

Auto Save: onFocusChange (Ha megnyitsz egy másik fájlt, akkor automatikusan ment.); Font Size: 14; Multi Cursor Modifier: ctrlCmd; Word Wrap: On;

## Hotkeys

A kódodat az alt+shift+F-el tudod automatikusan formázni.

HTML: html:5

JS: clg

File -> Auto save-t pipáld be.

Bal alul Settings->Settings->Text Editor -> Formatting->Foomat On Save-t pipáld be.

View -> Word Wrap (Alt+Z =Sor tördelés)

Hely foglaló szöveg: lorem50 tab

Emmet hivatalos dokumentációja https://code.visualstudio.com/docs/languages/emmet

Emmet Cheat Sheet https://docs.emmet.io/cheat-sheet/

Prettier beállítása:
⚙️ Alapértelmezett formázónak állítás Nyomd meg: Ctrl+Shift+P Írd be: Format Document With... Válaszd: Configure Default Formatter Állítsd: esbenp.prettier-vscode

💾 Format on Save bekapcsolása Menj: File → Preferences → Settings Keresőbe írd: format on save Pipáld be: Editor: Format On Save

Settings->Extensions->Prettier-> Tab Width:4

## VS Code kiegészítők listája

A felkiálltójellel ellátottak a legfontosabbak.

Angular Language Service (Segít Angular projektekben: hibák, kódkiegészítés, IntelliSense.)         
Angular Snippets (Version 18) (Kész Angular kódrészletek (ngFor, ngIf, component stb.).)                
Auto Close Tag!              
Auto Rename Tag!            
Bookmarks (Kódrészek megjelölése könyvjelzőként → gyorsabb navigálás.)      
Bootstrap 4, Font awesome 4, Font Awesome 5 Free (Gyors Bootstrap és ikon beillesztés.)     
Bootstrap 5 Quick Snippets (Gyors Bootstrap és ikon beillesztés.)           
Black Formatter (Python kódformázó.)            
Bracket Pair Color DLW (Beszínezi az egyező {} [] () párokat.)      
Code Spell Checker (Ellenőrzi a helyesírást kódban (pl. elgépelések változónévben).) !      
CodeSnap (Kódrészletből szép képet készít.)     
Colorful Comments (A kommenteket színesebbé teszi (// TODO, // WARNING).)!      
Todo Tree (A TODO-kat gyűjti össze az adott projektben.)        
Color Highlight (A CSS színeket kiemeli.)       
Copy Relative Path (Gyors másolása a fájl relatív elérési útvonalának.)     
CSS Peek (Ctrl+katt megmutatja, melyik CSS szabály vonatkozik az elemre.)!      
css-auto-prefix (Sok régi böngésző nem támogatja a modern css-t. Emiatt érdemes ezt letölteni.)     
ESLint (JavaScript hibakereső és szabály-ellenőrző.)            
Formatting Toggle (Ki/be kapcsolja a kódformázót (pl. Prettier).)           
Git History(Megmutatja a régi commitokat.)      
Git Project Manager (Projektkezelés Git-tel.)       
GitHub Copilot (A kódon belül segít neked, ne használd.)        
GitHub Copilot Chat (Ne használd.)      
GitHub Pull Requests (GitHub PR-ek kezelése.)       
GitLens - Git supercharged (Mindenre jó a Gitben: ki írta a sort, mikor, változások, diff-ek.)      
Image preview (Képek előnézete a kódban.)       
IntelliCode (Okosabb kódkiegészítés Microsofttól.)      
IntelliCode API Usage Examples(Okosabb kódkiegészítés Microsofttól.)        
JavaScript (ES6) code snippets (Hotkey, pl.: clg)           
Live Sass Compiler (SCSS → CSS automatikus fordítás.) Hogyan használd? https://youtu.be/eLmyLg2TcHc?si=fm0GC8UI4KZvHvDu&t=594       
Live Server!        
npm Intellisense (NPM csomagnevek automatikus kiegészítése.)!       
Playwright Test for VSCode (Webtesztek futtatása Playwrighttal.)        
Prettier - Code formatter!      
Project Manager!        
Quokka.js (Azonnal futtatja a JavaScript kódot, még mentés nélkül. De nem működik megfelelően a Ctrl+space)     
Restore Terminals       
Markdown All in One (Markdown fájl szerkesztéshez, tartalomjegyzék létrehozáshoz stb.)      
Csak dizájn, kinézet:       

One Dark Pro!       
Material Icon Theme!        
Power Mode Plus (Animációk gépelés közben. Csak szórakozás.) Az adatlapján menj a fogaskerékre ->   Powermode:Enabled.      
freeCodeCamp Dark Theme     
One Monokai Theme           

Java programozáshoz     

Debugger for Java       
Extension Pack for Java     
Gradle for Java 
Java        
Java Red Hat        
Maven for Java          
Mizu Icons (Dizájn!)        
Project Manager for Java        
Spring Boot Dahboard        
Test Runner for Java        

# HTML

A HTML (HyperText Markup Language) a weboldalak alapját adó leíró nyelv. Minden, amit egy weboldalon látsz – címek, bekezdések, képek, listák, táblázatok, űrlapok – HTML tagek segítségével jelenik meg. A HTML nem programozási nyelv, hanem egy szerkezetet leíró nyelv, amely megmondja a böngészőnek, hogy melyik elem mit jelent és hogyan épül fel a dokumentum.

A HTML tagek mindig valamilyen funkciót jelölnek: van, amelyik címsort hoz létre, van, amelyik egy szöveg bekezdést, listát vagy akár űrlapot. A tagek logikusan hierarchiába rendeződnek, így a böngésző és a keresőmotorok számára is érthetővé válik a dokumentum felépítése.

Az alábbiakban áttekintjük a leggyakrabban használt HTML elemeket, amelyek az alapját képezik minden modern weboldalnak.

Címsorok (Headings)
A HTML 6 különböző szintű címsort használ:

<h1> – a legnagyobb, főcím
<h2> – alcím
<h3> – kisebb alcím
…
<h6> – a legkisebb címsor
A címsorok hierarchiát adnak a dokumentumnak, és segítenek a keresőmotoroknak is a tartalom értelmezésében.

Bekezdés
A <p> tag hozza létre a bekezdéseket. A böngésző automatikusan ad körülötte egy kis térközt, így tagoltabbá és olvashatóbbá válik a szöveg.

Listák
A HTML kétféle listát használ:

Rendezetlen lista (unordered list)

<ul> – felsorolás, általában pontokkal
<li> – listaelem
Rendezett lista (ordered list)

<ol> – számozott lista
<li> – listaelem
Táblázatok
A táblázatok több részből állnak:

<table> – maga a táblázat
<thead> – a fejléc sorait foglalja magába
<tbody> – a tartalmi sorokat tartalmazza
<tr> – egy sor
<th> – fejléc cella (általában félkövér és középre igazított)
<td> – normál adatcella
Div
A <div> egy általános blokk szintű konténer, amelynek önmagában nincs szemantikai jelentése. Főként a szerkezet kialakítására és CSS alapú stílusozásra használjuk.

Űrlapok (Forms)
Az űrlapokat felhasználói adatok bekérésére használjuk:

<form> – maga az űrlap
action – ide küldi az adatokat a böngésző (pl. backend URL)
Gyakori mezők:

<label> – a mező címkéje
<input type="text"> – szöveg beviteli mező
<input type="password"> – jelszó mező
<input type="submit"> – küldés gomb
Gomb
A <button> tag egy kattintható gombot hoz létre. Lehet benne szöveg, ikon, vagy akár más HTML elem is.

Vízszintes vonal
A <hr> egy egyszerű vízszintes elválasztó vonal. Nincs záró tagje.

A label a for attribútumon keresztül kapcsolódik az input elemhez – pontosan az id alapján.

Ezekért hasznos:

Ha a felhasználó a "Text" feliratra kattint, ugyanaz történik, mintha a rádiógombot pipálná ki — mert össze vannak kapcsolva. Kisebb, mobilos vagy formában lévő elemek használhatóbbak ettől.

Kipróbálható ezeken a funkció:

 Text 
6
Kvízben előforduló speciális tagek
<area> – képtérkép része, mindig <map> tagben használjuk
<source> – videókhoz vagy hangfájlokhoz (<audio>, <video>)
<noscript> – akkor jelenik meg, ha a böngészőben le van tiltva a JavaScript
Kép
A képek megjelenítéséhez a következő taget használjuk:

<img src="..."> – maga a kép
src – a kép elérési útja
Opcionális tulajdonságok: width, height
Link
A linkekhez az <a href="URL"> taget használjuk. A href tartalmazza a cél URL-t.

Szövegformázó tagek
<b> – félkövér
<i> – dőlt
<u> – aláhúzott
<code> – kód jelölésére szolgál
Szerkezeti címkék
Header: fejléc (dokumentumé, vagy egy szelekció fejrésze).
Footer: lábléc, kiegészítő információk.
Main: domináns tartalom a lapon belül.
Aside: nem közvetlenül kapcsolódik a domináns tartalomhoz (pl.: oldalsáv, széljegyzet.).
Nav: navigációs rész, linkek csoportját tartalmazza.
Section: tartalmak elkülönítése (téma, szerepkör, funkció alapján).
Article: összetartozó tartalmi részek (pl.: cikk)
Kérdések és helyes válaszok
Melyik tag tartalmazza az <area> taget?
A helyes válasz: <map> tag.

Melyik tag tartalmazhatja a <source> taget?
A helyes válasz: <video> és <audio> tagek.

Kell-e záró tag a <hr> elemnek?
A <hr> tagnek nem kell záró tag.

Mikor jelenik meg a <noscript> tartalma?
A <noscript> akkor jelenít meg tartalmat, ha a JavaScript ki van kapcsolva vagy a böngésző nem támogatja.

Mit kell figyelembe venni, ha értéket akarunk elküldeni az adatbázisba?
Figyelni kell az input mező value attribútumára, a name attribútumra, valamint a submit gombra.

A <label> nem küld adatot, csak feliratként szolgál.

Emmet Cheat Sheet (HTML + CSS gyorsbillentyűk)
Alap dokumentum
! vagy html:5 → teljes HTML5 sablon:

<!DOCTYPE html>
        <html lang="en">
        <head>
          <meta charset="UTF-8">
          <title>Document</title>
        </head>
        <body></body>
        </html>
        
Szöveg és struktúra
p → <p></p>
h1 … h6 → <h1></h1> … <h6></h6>
ul>li*3 → <ul><li></li><li></li><li></li></ul>
ol>li*3 → <ol><li></li><li></li><li></li></ol>
dl>dt+dd → <dl><dt></dt><dd></dd></dl>
Linkek
a → <a href=""></a>
a:link → <a href="http://"></a>
a:mail → <a href="mailto:"></a>
Képek
img → <img src="" alt="">
img:s → <img srcset="" src="" alt="">
picture>source:srcset+img → <picture><source srcset=""><img src="" alt=""></picture>
Űrlapok
form → <form action=""></form>
form:get → <form action="" method="get"></form>
form:post → <form action="" method="post"></form>
input → <input type="text">
input:s → <input type="submit" value="">
input:r → <input type="radio" name="" id="">
input:c → <input type="checkbox" name="" id="">
textarea → <textarea name="" id="" cols="30" rows="10"></textarea>
select+ → <select name="" id=""><option value=""></option></select>
Szekciók
header → <header></header>
footer → <footer></footer>
main → <main></main>
section → <section></section>
article → <article></article>
aside → <aside></aside>
nav → <nav></nav>
Táblázatok
table+ → <table><tr><td></td></tr></table>
tr+ → <tr><td></td></tr>
Import-ok
link:css → CSS importáláshoz.
script:src → JS importáláshoz.
Az Emmet egy kódbővítő eszköz, amellyel rövid parancsokból automatikusan teljes HTML vagy CSS kódot tudsz generálni.

HTML Emmet parancsok
! → teljes HTML5 alap sablon
div → <div></div>
.box → <div class="box"></div>
#header → <div id="header"></div>
ul>li → beágyazott listaelem
ul>li*5 → 5 darab li elem
div>p>span → hierarchia
p{Hello} → <p>Hello</p>
a[href="#"] → attribútumos elem
Item numbering: $
Példa számozott listaelemre:

ul>li.item$*5
<ul>
    <li class="item1"></li>
    <li class="item2"></li>
    <li class="item3"></li>
    <li class="item4"></li>
    <li class="item5"></li>
</ul>
Multiplication: *
Példa ismétlésre:

ul>li*5
<ul>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
</ul>
Speciális Emmet elemek
a:link → <a href="http://"></a>
a:mail → <a href="mailto:"></a>
link:css → <link rel="stylesheet" href="style.css" />
script:src → <script src=""></script>
mg → <img src="" alt="" />
CSS Emmet parancsok
m10 → margin: 10px;
p20 → padding: 20px;
bd1-s → border: 1px solid;
fw700 → font-weight: 700;
fs18 → font-size: 18px;
bgc#333 → background-color: #333;
c#fff → color: #fff;
d:f → display: flex;
jc-sb → justify-content: space-between;
Forrás: Emmet hivatalos dokumentáció – Cheat Sheet https://docs.emmet.io/cheat-sheet/

# CSS

CSS szelektorok:

Az univerzális szelektor (*) minden HTML-elemet kijelöl.
Az #id szelektor csak egy elemet jelölhet.
A csoportosított szelektor (h1, h2, p) több elemet is kijelöl.
CSS tulajdonságok:

padding: belső térköz
width: szélesség
margin: külső térköz
font-weight: betűvastagság
A position: fixed; rögzíti az elemet a viewporthoz.

CSS (Cascading Style Sheets) – Lépcsőzetes stíluslapok

A CSS egy stílusleíró nyelv, amely HTML, XML vagy SVG alapú dokumentumok megjelenését (pl. színek, betűtípusok, elrendezés, margók stb.) határozza meg.

A „lépcsőzetes” elnevezés arra utal, hogy a stílusok öröklődnek és felülírhatók: ha több stílus vonatkozik egy elemre, a böngésző bizonyos szabályok szerint dönti el, melyik érvényesüljön.

A CSS önmagában nem programozási nyelv, tehát logikát (pl. változókat, függvényeket, feltételeket) közvetlenül nem tartalmaz.

Alapvetően, így néz ki:

selector { deklaráció; -> tulajdonság neve: tulajdonság értéke; }

Viszont léteznek kiterjesztései, mint például:

Sass (Syntactically Awesome Style Sheets)
Less
Ezek lehetővé teszik, hogy változókat, ciklusokat, függvényeket használjunk, és logikusabban, modulárisan építsük fel a stílusokat. A böngésző ezeket lefordított (kompilált) CSS fájlként kapja meg.

box-sizing
Flex elrendezés:

Flexbox egy dimenzióban működik: sorban vagy oszlopban. A float régi technika, eredetileg szöveg körbefolyatása miatt találták ki.

Flex paraméterek:

flex: grow shrink basis
Pl.: flex: 0 0 70%
grow = 0 → nem nő
shrink = 0 → nem zsugorodik || shrink = 1 → alaphelyzetben összezsugorodhat, ha kisebb a hely
basis = 70% → alapértelmezett szélesség 70%
Float elrendezés:

Ha float-tal két dobozt egymás mellé akarsz tenni, gyakran kell clearfix trükk, külön üres <div> vagy ::after pseudo-element a „töréshez”.

Grid elrendezés:

Ha komplexebb layoutot akarsz, pl.: több sor és több oszlop, vagy mobilon a main és aside egymás alá kerül, a Grid sokkal rugalmasabb. A reszponzív dizájn miatt kell a grid.

HTML szemantikus formázó (inline) tagek

Tag	Jelentés magyarul	Mire utal (szemantika)
<strong>	kiemelés, hangsúlyos szöveg	fontos információ (nem csak vastag betű)
<em>	dőlt kiemelés	nyomatékosítás, hangsúlyváltás beszédben
<mark>	kiemelt, kiemelés sárgával	releváns szöveg jelölése (pl. keresési találat)
<small>	apróbetűs szöveg	jogi, megjegyzés, mellékinformáció
<cite>	mű címe	könyv, film, zene, műalkotás neve
<q>	idézet	rövid idézet, automatikus idézőjel
<blockquote>	hosszabb idézet	külön bekezdésben idézett szöveg
<abbr>	rövidítés	pl. HTML (title: HyperText Markup Language)
<dfn>	definíció	először bevezetett fogalom
<time>	időpont, dátum	gépek számára érthető dátum
<code>	kód	programkód jelölése
<kbd>	billentyűzet bevitel	pl. Ctrl + C
<samp>	programkimenet	parancssori eredmények
<del>	törölt szöveg	változtatás, verziózás
<ins>	beszúrt szöveg	új tartalom jelölése

CSS Selectors (W3 School) https://www.w3schools.com/cssref/css_selectors.php

HTML Selector


    /* Globális elemek / h1, h2, h3, h4, h5, h6, p, ul, li, ol {  
        /* Ezekre az elemekre egységes stílust adunk */
        color: rgb(45, 173, 228); /* Világoskék szöveg */
        text-shadow: 2px 2px #22096b; /* Sötétkék árnyék */
    } /* Globális elemek vége */

    /* Saját betűkészlet importálása */
    @font-face { /* Egyedi fontot töltünk be */
        font-family: "Momo Signature"; /* A betűkészlet neve */
        /* Fizikai elérési út */
        src: url("../../Assets/Fonts/Momo_Signature/MomoSignature-Regular.ttf") format("truetype"); 
    }

     /*A betűk árnyékát sötét kékre állítjuk: */
    text-shadow: 2px 2px #22096b;

    /* Body alapbeállítások */ 
    body {
        background-color: black; /* Az oldal háttere fekete */
        
        /* Betűtípus beállítás: saját font + tartalékok */
        font: normal 16px "Momo Signature", "Special Elite", serif; 
        line-height: 1.6em; /* Sorok közti távolság */
        margin: 10px; /* Külső margó */
        padding: 20px; /* Belső térköz */
        background-image: url("../../Assets/Images/guitar.jpg"); /* Háttérkép */
        background-repeat: no-repeat; /* Ne ismételje a képet */
        background-position: center top; /* Kép középre igazítva felül */
    }

    /* Képek és dobozok */
    .box-2 img {
        margin: 10px; /* Kép körüli külső margó */
        border: 10px solid #875033; /* Barna keret a kép körül */
    }

    .box-1 {
        opacity: 0.9; /* Enyhén átlátszó doboz */
    }

    /* Konténer elrendezés */
    .container {
        width: 960px; /* Fix szélesség */
        margin: auto; /* Középre igazítás */
        padding: 5px; /* Belső térköz */
        display: flex; /* Flexbox elrendezés */
    }

    @media (max-width: 600px) { /* Mobilbarát szabály */
        .container {
            width: 100%; /* Teljes szélesség mobilon */
            margin: 20px; /* Nagyobb margó mobil nézetben */
        }
    }

    /* Header és Footer */
    #headerID {
        text-align: center; /* Középre igazított szöveg */
        background-color: rgb(60, 77, 233); /* Kék háttér */
        color: white; /* Fehér szöveg */
        padding: 10px; /* Belső térköz */
    }

    #footerID {
        text-align: center; /* Középre igazítás */
        font-size: 26px; /* Nagy szöveg */
        color: cyan; /* Cián szín */
    }

    /* Linkek stílusai */
    a {
        color: cyan; /* Link szín (első szabály – felülíródik!) */
        text-decoration: none; /* Link aláhúzás kikapcsolása */
    }

    a {
        color: rgb(51, 138, 238); /* Második szabály – ez írja felül az előzőt */
        text-decoration: none;
    }

    a {
        color: red; /* Harmadik szabály – ismét felülírja */
        text-decoration: underline; /* Aláhúzott link */
    }

    a {
        color: yellow; /* Végső érvényes szín */
        text-decoration: underline; /* Végső érvényes stílus */
    }

    /* Gombok */
    button, .new_form input[type="submit"], .fix_button {
        background-color: blueviolet; /* Lila gomb */
        font-family: "Special Elite", serif; /* Betűtípus */
        padding: 8px 15px; /* Belső térköz */
        border: none; /* Keret nélkül */
    }

    /* Űrlapok */
    .new_form input[type="text"], 
    .new_form input[type="password"], 
    .new_form textarea {
        margin-top: 2px; /* Felső margó */
        margin-bottom: 5px; /* Alsó margó */
        padding: 10px; /* Belső térköz */
        width: 100%; /* Teljes szélesség */
    }

    /* Szekciók */
    section {
        border: 3px magenta solid; /* Magenta keret */
        margin-bottom: 20px; /* Alsó térköz */
        color: rgb(231, 231, 50); /* Sárgás szöveg */
        padding: 5px; /* Belső tér */
        border-radius: 10px; /* Lekerekített sarkok */
    }

    /* Navigáció és fix gombok */
    .navigation_button, .fix_button {
        position: fixed; /* Fixen a viewporthoz rögzítve */
        left: 0px; /* Bal szél */
        top: 200px; /* Fentről 200px */
        font-size: 25px; /* Nagy betűméret */
        background-color: aquamarine; /* Kékeszöld háttér */
        border-top: 1px solid rgb(247, 243, 251); /* Felső keret */
    }

    /* Lista stílus */
    ul, ol, li {
        color: blueviolet; /* Lila szöveg a listákban */
    }

    /* Táblázatok */
    tr, td, th {
        border: 1px solid white; /* Fehér keret cellák körül */
        color: white; /* Fehér szöveg */
    }

    /* Formázott dobozok */
    .block {
        margin-top: 10px; /* Felső margó */
        float: left; /* Egymás mellé igazítás */
        width: 33.33%; /* Három doboz fér ki egy sorba */
        border: 1px solid #e514de; /* Rózsaszín keret */
        padding: 10px; /* Belső tér */
        box-sizing: border-box; /* Padding is beleszámít */
    }

    .clearfix {
        clear: both; /* Float törlése, elkerülve az összeomlást */
    }

    /* Motivációs doboz */
    .motivation-box {
        width: 200px; /* Szélesség */
        height: 200px; /* Magasság */
        border: 1px solid #e514de; /* Rózsaszín keret */
        margin-top: 10px; /* Felső margó */
        position: relative; /* Gyerek elemek relatív pozicionálása */
    }

    .motivation-box h1 {
        position: absolute; /* A dobozon belül szabadság */
        top: 10px; /* Fentről 10px */
        left: 10px; /* Balról 10px */
    }

    /* Contact form */
    .contact_form {
        background-color: black; /* Fekete háttér */
        color: magenta; /* Magenta betűszín */
        padding: 20px; /* Belső tér */
        border: 3px solid magenta; /* Külső keret */
        margin: 40px; /* Külső margó */
        border-right: 10px solid magenta; /* Jobb oldali vastag keret */
        border-left: 10px dotted magenta; /* Bal oldali pontozott keret */
        margin-bottom: 20px; /* Alsó margó */
    }

    /* Pszeudo-osztályok linkekhez */
    .test_link {
        text-decoration: line-through; /* Áthúzott link */
    }

    .test_link {
        color: red; /* Piros link – felülíródik később */
    }

    .test_link {
        color: white; /* Végső szín: fehér */
    }

    /*Saját szím változó*/
    :root {
    --my-primary-color: #3498db; /* saját színváltozó */
    --my-secondary-color: rgb(255, 99, 71); /* másik példa */
    }

    /*A var() függvénnyel hívod meg.*/
    body {
    background-color: var(--my-primary-color);
    color: var(--my-secondary-color);
    }

    h1 {
    color: var(--my-accent-color, purple); /* ha nincs --my-accent-color, akkor lila lesz */
    }

    
# Tailwind

Ezt a framework-ot, akkor kezd el használni, amikor magabiztos a css tudásod.

A head részre ezt másold be:

<script src="https://cdn.tailwindcss.com"></script>
Tailwind background snippet gyűjtemény:

https://tailkits.com/components/tailwind-background-snippets/

# JavaScript

Objektum orientált, prototípus alapú szkript nyelv. Leginkább a weboldalak kliens oldali logikájára használják. Weboldal kliensen futó programja.

Magas szintű programozási nyelv. Nem kell foglalkozni a memória felszabadítással.

Interpretált vagy fordított?

Bár a JavaScriptet hagyományosan interpretált nyelvnek nevezzük (mert nem kell manuálisan fordítani, mint a Javát a javac paranccsal), a modern böngészők (mint a Chrome V8 motorja) a háttérben már JIT (Just-In-Time) kompilálást használnak. Ez azt jelenti, hogy a böngésző futtatás közben elemzi és fordítja gépi kódra a JavaScriptet a maximális sebesség érdekében. Fejlesztőként ebből annyit érzékelsz, hogy a kód azonnal fut, amint elmented és frissíted a böngészőt.

Multi-paradigma, vagyis többféleképpen is megírhatod a programodat, pl.: objektum orientált módon.

Régebben LiveScript volt a neve. Mocha → LiveScript → JavaScript (1995)

ECMAScript = a nyelvi szabvány; a JavaScript ennek a szabványnak egy implementációja.

A </body> elé kell beírni a script taget, mert a böngésző fentről lefelé tölti be az oldalt.

A JavaScript a weboldalak működéséért felelős programozási nyelv. Segítségével dinamikus elemeket hozhatunk létre, adatokat dolgozhatunk fel, eseményeket kezelhetünk (kattintás, billentyűlenyomás), vagy akár teljes alkalmazásokat építhetünk.

Míg a HTML a szerkezetet, a CSS a kinézetet adja, addig a JavaScript teszi interaktívvá a weboldalt. A böngésző minden JS sort sorban végrehajt.

Alap utasítások
Egyszerű kiíratások, hibák, figyelmeztetések megjelenítése:

alert('Hello!') – felugró ablak
console.log() – üzenet az ellenőrző konzolba
console.error() – hibaüzenet
console.warn() – figyelmeztetés
Változók
A változókban adatokat tárolunk. JavaScriptben a leggyakoribb típusok:

let – módosítható változó, csak a blokkon belül él (ajánlott)
const – állandó, értéke nem módosítható
var – régi változótípus, kerülendő (újradeklarálható, problémás)
Példa:

let kor = 20;
kor = 21; // módosítható

const szam = 10;
// szam = 11;  // hiba: a const nem módosítható
Adattípusok
Két nagy csoportjuk van: primitív típusok és objektum típusok.

Primitívek
String – szöveg
Number – szám (egész és tizedes is)
Boolean – igaz vagy hamis
null – szándékosan „nincs érték”
undefined – létrehozott változó, de nincs értéke
Példa:

const nev = "Zsolt";
const kor = 21;
const suly = 80.5;
const felnott = true;

const x = null; 
const y = undefined;
A null és az undefined gyakran keveredik, de fontos a különbség:

null – Te állítod be, hogy „nincs érték”.
undefined – A böngésző adja, ha nem kap értéket a változó.
Objektumok
A JavaScript objektumok sok adatot tartalmazhatnak egy helyen.

Példa dátum objektumra:

const date = new Date();          // mai dátum
const date2 = new Date("2025-11-24");
String műveletek
A szövegekkel gyakran végzünk műveleteket:

text.length – megadja a hosszát
text.toLowerCase() – kisbetűssé alakítja
text.substring(1,5) – részlet kivágása
text.split() – darabolás
Példa modern string írásra (interpoláció):

const szoveg = "Hello világ";
console.log(`${szoveg}!`);
Dátumok kezelése
getDate() – nap lekérése
getDay() – hét napja (0–6)
getMonth() – hónap (0–11)
setHours() – óra beállítása
setFullYear() – év beállítása
toISOString() – ISO formátumú dátum
Műveletek
A JavaScript támogatja a matematikai műveleteket, például:

+= – növeli a változó értékét
++ – egyesével növel
let szam = 10;
        szam += 10;  // 20
        szam++;      // 21
Feltételek
Az if utasítással elágazásokat hozhatunk létre.

Példa:

const a = 14;
        const b = 10;

        if (a <= b) {
            console.log("Igaz");
        } else {
            console.log("Hamis");
        }

        if (a === b) {  // szigorú összehasonlítás (típust is nézi)
            console.log("Egyenlő");
        } else {
            console.log("Nem egyenlő");
        }
A === mindig ajánlott a == helyett, mert típust is ellenőriz.

Kérdések és helyes válaszok
Hogyan lehet egy szöveg hosszát lekérdezni?
szoveg.length

Melyik állítás igaz a JSON-re?
Nyelvfüggetlen.

JSON (JavaScript Object Notation) adatcsere-formátum, ami bármilyen nyelven használható (Java, Python, C#, stb.), nem csak JavaScript-ben.

Nem kompatibilis 100%-ban XML-lel, mert az teljesen más szintaxis.

Mely állítások igazak a BOM-ra?
Hierarchikus elrendezésű, a tetején a window object helyezkedik el.

Segítségével elérjük a böngésző tulajdonságait, beállításait (ablakméret, előzmények, URL-ek stb.).

A BOM (Browser Object Model) nem szabványos, de minden böngésző implementálja.

Lehetővé teszi az ablak, előzmények, URL-ek, képernyőméret kezelését, a dokumentumon kívüli objektumokhoz fér hozzá.

Mi a kimenete?
        let keresztNev = "Elek";
        let csaladNev = null;
        let beceNev = null;
        console.log(keresztNev ?? csaladNev ?? beceNev ?? "Nem meghatározott");
            
Megoldás: Elek

Az ?? (nullish coalescing) a null vagy undefined ellenőrzi. keresztNev értéke "Elek", ami nem null vagy undefined, így az első érték kerül kiírásra.

Mi a kimenete?
console.log(Math.ceil(4.4))
Megoldás: 5

Mindig a következő egész számra kerekít felfelé.

Mely állítások igazak a JSON-re?
Nyelvfüggetlen.

Adatok tárolására és az adatküldés leegyszerűsítésére használható.

A JSON formátum adatcsere-formátum, kliens-szerver kommunikációban is gyakran használják.

Mit ír ki?
                        let obj = {
                            for: 1,
                            let: 2,
                            return: 3,
                        }
                        console.log(obj.let);
                       
Megoldás: 2

Objektumokban kulcsokat szabad szövegesen használni, így let itt egy érvényes property. obj.let pontosan a 2 értéket adja vissza.

Mi a kimenete?
                    let nameSymbol2 = Symbol("name");
                    console.log(Symbol.keyFor(nameSymbol2));
                      
undefined

Symbol("name") egy lokális szimbólum, ami nem regisztrált globális szimbólumként.

A Symbol.keyFor() csak a globális szimbólumoknál ad vissza kulcsot.

Mi a kimenete?
                    var foo = function teszt(){
                        console.log(foo==foo)
                    };
                    foo();
            
true

foo mindig önmagára mutat a függvény scope-on belül, így a foo == foo mindig true.

Mi a kimenete?
console.log(undefined > 0);
false

undefined nem szám, így összehasonlításkor NaN-ra konvertálódik → minden összehasonlítás false lesz.

Nem dob hibát, egyszerűen false az eredmény.

A folytatáshoz bal oldalt válaszd ki a javascript fejezetet.


# Felhasznált források és ajánlott linkek 

SanFranciscoboljöttem.com - Blog és kurzusok https://sanfranciscoboljottem.com      
SZTE - Java Objektumok és Osztályok https://okt.inf.szte.hu/prog1/gyakorlat/eloadas/Java/objectsAndClasses/     

YouTube - Fullstack Tutorial sorozat https://www.youtube.com/watch?v=8qMi3e_fzKc&list=PL92V_WHHt2CnXaUIA9T2ww7peDK4lqmZj        


IT Szótár - Mi az a JVM? https://itszotar.hu/       jvm-java-virtualis-gep-mi-a-mukodese-es-mi-a-szerepe-a-java-kod-futtatasaban/       

The Complete JavaScript Course 2025: From Zero to Expert!
https://www.udemy.com/course/the-complete-javascript-course/

A jegyzetek és magyarázatok a fenti források alapján készültek tanulási céllal.

© 2026 Nagraggini (Freud Andrea) — Minden jog fenntartva.