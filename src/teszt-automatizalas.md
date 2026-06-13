# Teszt automatizálás

**Ezeket használják manapság**

Playwright (nagyon modern, Udemy-n jó kurzusok vannak)
Cypress (frontend fókuszú)
Ranorex  -Az oldala kifejetezzen segít: support.ranorex.com + (Udemy)
Automatizált Teszt Keretrendszer (ATF)

# Weboldalak, amiket lehet tesztelni

[Utest.com](https://www.utest.com/resources)            
[API tesztelés videókurzus](https://www.youtube.com/watch?v=hvSlWnLiK_U&list=PLimzEeSv6f4Vk6cXGpoGU2ZhNcyI5rzTp)        
[UI test playground (the internet)](https://the-internet.herokuapp.com/)
[UI Test Automation Playground](http://www.uitestingplayground.com/)
[Automation Exercise (UI and Api test)](https://automationexercise.com/)
[Api test](https://app.reqres.in/)
[Demo webshop](https://demowebshop.tricentis.com/)
[Bank fiók ](https://parabank.parasoft.com/)
[HR-szoftver](https://opensource-demo.orangehrmlive.com/)

## Selenium

A Selenium-ot érdemes először kezdőként használni és után tovább menni a bonyolultabbak felé.

### Selenium alapfogalmak

**Selenium WebDriver**

- Programozható tesztautomatizálási eszköz.
- Támogatja a legtöbb böngészőt (Chrome, Firefox, Edge stb.).
- Több nyelven is használható: Java, Python, C#, JavaScript stb.
- Fejlesztők és tesztelők írhatnak benne automatizált funkcionális/regressziós teszteket.


**Selenium Grid**

- Lehetővé teszi a párhuzamos tesztfuttatást több gépen és böngészőn.
- Hasznos, ha sok tesztet kell rövid idő alatt lefuttatni.
- Két fő része van:
    Hub: Központ, ami elosztja a feladatokat.
    Node-ok: A gépek, ahol a tesztek ténylegesen futnak.


Selenium tesztek típusai
1. Rögzítés és visszajátszás (Record & Playback)
   
- Ezt a funkciót a Selenium IDE biztosítja.
- A felhasználói műveleteket automatikusan rögzíti (kattintás, beírás, navigáció stb.).
- Utána visszajátszható, így gyorsan lehet egyszerű teszteket készíteni.
- Nem igényel programozási tudást, de kevésbé rugalmas.


2. Programozott tesztelés (WebDriver)
   
- Itt kódban írjuk meg a teszteket.
- Rugalmas, skálázható, integrálható CI/CD folyamatokba (pl. Jenkins).

Assert -> Ha a feltétel nem teljesül, a teszt megáll. -> Kritikus ellenőrzésekhez
Verify -> Ha a feltétel nem teljesül, a teszt tovább fut, de jelzi a hibát. -> Nem kritikus hibákhoz

**Selenese**

A Selenium IDE saját nyelve/parancskészlete.
Egyszerű parancsokat használ, pl.: open, click, type, verifyText
Támogat kommenteket is (pl. // jellel).

A Selenium Webdriver használatóról a gyakorlásaimat és jegyzeteimet [itt](https://github.com/Nagraggini/selenium-playground) találod.

További projektjeim:
[sauce-demo](https://github.com/Nagraggini/sauce-demo)
[automation-exercise](https://github.com/Nagraggini/automation-exercise)

# QA (tesztautomatizálás)

**Manuális vs automatizált tesztelés**

Manuális tesztelés:     
- UX/UI, kinézet, felhasználói élmény       
- ad-hoc / exploratory tesztelés        
- gyors validáció új feature-re     

Automatizált tesztelés:     
- ismétlődő tesztek (regresszió)        
- stabil funkciók ellenőrzése       
- gyors visszajelzés CI-ben     
- UI-t is lehet automatizálni       

Fontos      
➡️ amit sokszor futtatsz → automatizáld     

**Framework felépítése**

Test layer – maga a teszt (JUnit/TestNG).            
Page Object Model (POM) – UI elemek és műveletek külön osztályokban.
    Ha változik a HTML, nem kell minden tesztet átírni, csak ezt az egy osztályt.           
Utility réteg – pl. wait-ek, config, logger.  
    Ez az újrahasznosítható segédkód.
Driver kezelés – WebDriver setup/teardown.    
    Böngésző indítása és leállítása.

👉 Példa stack:

Java + JUnit/TestNG     
Selenium        
Maven/Gradle        

**CI/CD**

CI (Continuous Integration):        
    minden commit után build + teszt fut  

CD (Continuous Delivery/Deployment):        
    automatikus release pipeline        

👉 Kapcsolat:
    automatizált tesztek a pipeline részei
    ha teszt fail → build fail

**Az automatizált tesztelésben gyakran ezek a teszttípusok jönnek elő:**

- Unit teszt – egy kis egységet vizsgál, például egy metódust vagy osztályt.
- Integration teszt – több komponens együttműködését ellenőrzi.
- End-to-End (E2E) teszt – teljes felhasználói folyamatot vizsgál elejétől végéig.
- Regression teszt – azt ellenőrzi, hogy egy módosítás nem rontott-e el korábban működő funkciókat.
- Smoke teszt – gyors alapellenőrzés, hogy a rendszer fő funkciói működnek-e.
- Sanity teszt – kisebb módosítás után célzott ellenőrzés, hogy az adott javítás rendben van-e.
- UI teszt – felhasználói felület elemeinek működése és megjelenése.
- API teszt – backend szolgáltatások, végpontok, request/response ellenőrzése.
- Performance teszt – sebesség, válaszidő, terhelhetőség vizsgálata.
- Load teszt – normál vagy nagy terhelés alatti viselkedés.
- Security teszt – jogosultságok, adatvédelem, sebezhetőségek vizsgálata.
- Acceptance teszt (UAT) – annak ellenőrzése, hogy az üzleti igények teljesülnek-e.