Tematika a tesztelés gyakorlásához
1. Saját fejlesztésű hardver és szoftver tesztelése, hibák rögzítése
Szoftvertesztelés alapjai: Kézi tesztelés (funkcionális, regressziós, integrációs tesztek).
1.1 A tesztelés, mint a szoftverfejlesztés hajtóereje
A TDD, ATDD és BDD hasonló fejlesztési megközelítések, ahol a tesztek meghatározása a fejlesztés irányításának eszközeként szolgál. Mindegyik megközelítés megvalósítja a korai tesztelés elvét és követi a shift left megközelítést, mivel a tesztek meghatározása előbb történik, mint a kód megírásra. Ezek a megközelítések az iteratív fejlesztési modellt támogatják és az alábbiak szerint lehet jellemezni őket:

Tesztvezérelt fejlesztés (TDD):

A kódolást tesztesetek irányítják (az átfogó szoftvertervek helyett) (Beck 2003)
Először a tesztek kerülnek megírásra, majd azt követően a kód, olyan módon, hogy a teszteknek megfeleljen. Végül a teszteket és a kódot is refaktorálják.
Elfogadásiteszt-vezérelt fejlesztés (ATDD):

A teszteket elfogadási feltételekből származtatja a rendszertervezési folyamat részeként (Gärtner 2011)
A teszteket az előtt írják meg, hogy lefejesztésre kerülne az alkalmazás azon része, mely kielégíti ezeket a teszteket.
Viselkedésvezérelt fejlesztés (BDD):

Kifejezi az alkalmazás kívánt viselkedését olyan tesztesetekkel, melyek egyszerű formában, természetes nyelven vannak megírva, és így könnyen érthető az érdekelt felek számára – általában a "Given/When/Then" formát használva (Chelimsky 2010).
A teszteseteket ezután automatikusan végrehajtható tesztekké alakítják.
A fent említett megközelítések alkalmazása során, a tesztek megmaradhatnak automatizált tesztek formájában, hogy biztosítsák a kód minőségét jövőbeli módosítások esetén.

1.2 DevOps és tesztelés
DevOps egy szervezeti megközelítés, melynek célja a szinergia létrehozása a fejlesztés (beleértve a tesztelést) és az üzemeltetés között, hogy közös célokat érjenek el. A DevOps egy kulturális változást igényel a szervezeten belül, hogy áthidalja a fejlesztés (beleértve a tesztelést) és az üzemeltetés közötti réseket, miközben azok szerepét egyenértékűnek tekinti. A DevOps támogatja a csapat önállóságát, a gyors visszajelzést, az integrált eszközrendszerrel való munkát, valamint olyan technikai gyakorlatokat, mint a folyamatos integráció (CI) és a folyamatos szállítás (CD). Ez lehetővé teszi a csapatok számára, hogy a DevOps szállítási folyamatláncon (delivery pipeline) keresztül gyorsabban készítsenek, teszteljenek és adjanak ki magas minőségű kódot (Kim 2016).

A tesztelés szempontjából nézve a DevOps néhány előnye:

Gyors visszajelzés a kód minőségéről és arról, hogy a változtatások hogyan befolyásolják a már meglévő kódot.
A folyamatos integráció elősegíti a shift left megközelítést a tesztelésben, mivel bátorítja a fejlesztőket, hogy jó minőségű kódot adjanak át, komponenstesztekkel és statikus elemzéssel kísérve.
Támogatja az automatizált folyamatokat, mint például a folyamatos integrációt/szállítást, amelyek segítik a stabil tesztkörnyezetek kialakítását.
Növeli a fókuszt a nemfunkcionális jellemzőkön (pl. teljesítmény, megbízhatóság).
Az automatizálás a szállítási folyamatláncon keresztül csökkenti az ismétlődő manuális tesztek szükségességét.
Minimális a regresszió okozta kockázat az automatizált regressziós tesztek méretének és hatókörének köszönhetően.
A DevOps sem mentes a kockázatoktól és kihívásoktól, például:

A DevOps szállítási folyamatláncot (delivery pipeline) meg kell tervezni és meg kell valósítani.
A folyamatos integrációs/szállítási eszközöket be kell vezetni és karban kell tartani.
A tesztautomatizálás további erőforrásokat igényel, illetve nehéz lehet kialakítani és karbantartani.
Bár a DevOps megköveteli egy magasabb fokú automatizált tesztelés megvalósítását, a manuális tesztelés – különösen a felhasználó szempontjából – továbbra is szükséges.

1.3 A shift left megközelítés
Az korai tesztelés elve éha shift left néven is említésre kerül. A shift left esetén az a cél, hogy a szoftverfejlesztés életciklusának folyamatában a tesztelés minél korábban legyen elvégezve (pl. nem várni a kód megvalósítására vagy a komponensek integrálására). Viszont ez nem jelenti azt, hogy a szoftverfejlesztés életciklusának későbbi szakaszaiban a tesztelés elhanyagolható lenne.

A tesztelésben a shift left megvalósítását elősegítő számos jó gyakorlat létezik, mint például:

Specifikációk felülvizsgálata a tesztelés szempontjából. Ezek a felülvizsgálatok gyakran fedeznek fel lehetséges hibákat, amik például félreértésekből, hiányosságokból vagy ellentmondásokból származnak.
Tesztesetek megírása a kód létrejötte előtt, majd a kód futtatása egy teszttámogató szoftverkörnyezetben a kód implementálása közben.
Folyamatos integráció és még jobb esetben folyamatos szállítás alkalmazása, mivel ezek gyors visszajelzést adnak, illetve automatizált komponensteszteket biztosítanak a kód mellé, amikor azok tárolóba (repository) kerülnek.
A forráskód statikus elemzése a dinamikus tesztelés előtt, vagy egy automatizált folyamat részeként.
Nemfunkcionális tesztelés megvalósítása, lehetőség szerint komponensteszt-szinten kezdve. Ez egy formája a shift left megvalósításának, mert a nemfunkcionális teszttípus általában a szoftverfejlesztési életciklus későbbi részeiben történik, mikor a teljes rendszer és egy reprezentatív tesztkörnyezet már a rendelkezésünkre áll.
A shift left megközelítés extra képzést, költségeket eredményezhet a folyamat korai szakaszaiban, de várható, hogy a későbbiekben megtakarításhoz vezet.
A shift left megközelítéshez fontos, hogy az érdekelt felek elkötelezettek legyenek a koncepció irányában.

1.4 Tesztelési típusok
Számos teszttípus létezik és alkalmazható egy projektben. Ebben a tantervben a következő négy teszttípust említjük meg:
Funkcionális tesztelés: A komponens vagy rendszer működését vizsgáljuk abból a szempontból, hogy elvégzi-e a meghatározott funkcióit.
A fő céljai: funkcionális teljesség, helyesség, megfelelőség ellenőrzése.
Nemfunkcionális tesztelés: Olyan tulajdonságokat ellenőrzünk, amelyek nem a komponens vagy rendszer funkcionális jellemzői.
A fő cél: nemfunkcionális szoftver-minőségjellemzők ellenőrzése (ISO/IEC 25010 szabvány szerint):
Teljesítményhatékonyság
Kompatibilitás
Használhatóság
Megbízhatóság
Biztonság
Karbantarthatóság
Hordozhatóság
Előfordulhat, hogy a nemfunkcionális tesztelés az életciklus korai szakaszában kezdődik (például a felülvizsgálatok, a komponenstesztelés vagy a rendszertesztelés részeként). Számos nemfunkcionális teszt származtatható funkcionális tesztekből, mivel egy már létező funkcionális teszt futtatása során ellenőrizhetünk nemfunkcionális jellemzőket is (például ellenőrizhetjük, hogy egy funkció végrehajtásához szükséges idő megfelelő-e, vagy végrehajtódik-e egy eltérő keretrendszeren belül). A későn megtalált nemfunkcionális hibák nagyban befolyásolhatják egy projekt sikerét. Nemfunkcionális tesztelés esetén néha szükségünk lehet specifikus tesztkörnyezetre, mint például használhatósági teszt esetén egy használhatósági laborra.

Feketedoboz tesztelés: Specifikációalapú teszttípus, ahol a teszteseteket a rendszer specifikációiból származtatjuk. Fő cél: a rendszer viselkedésének ellenőrzése a rendszer specifikációinak szempontjából.
Fehérdoboz tesztelés: Struktúraalapú teszttípus, ahol a rendszer belső szerkezete vagy az implementációja (például: kód, architektúra, munkafolyamat, adatfolyam) alapján származtatjuk a teszteseteket. A fehérdoboz tesztelés fő célja, hogy tesztekkel elfogadható szinten lefedjük a rendszer alapvető struktúráját.
Mind a négy teszttípus alkalmazható minden tesztszinten, bár a fókusz minden szinten más lesz. Számos különböző teszttechnika használható a tesztfeltételek és tesztesetek származtatására minden teszttípus esetében.

1.5 Ellenőrző és regressziós tesztelés
Változásokat tipikusan akkor eszközölünk egy komponensen vagy rendszeren, mikor új funkcionalitásokat szeretnénk bevezetni vagy hibákat szeretnénk javítani. A tesztelésnek ebben az esetben ellenőrző és regressziós tesztelést is tartalmaznia kell.

Az ellenőrző tesztelés megerősíti, hogy az adott hiba sikeresen javítva lett. A kockázattól függően, a javított szoftververziót több módon is tesztelhetjük:
újrafuttatva az összes tesztesetet, amelyek korábban elbuktak az adott hiba miatt, vagy
kiegészítve a tesztfuttatást új tesztekkel, amelyek lefedik a javítás által bevezetett módosításokat is
Azonban, mikor hibajavítás során a rendelkezésre álló erőforrások (idő és pénz) nem elegendőek, az ellenőrző tesztelés korlátozódhat csak a meghibásodást előhozó lépések megismétlésére, és annak ellenőrzésére, hogy a meghibásodás nem történik meg.

A regressziós tesztelés megerősíti, hogy egy változtatásnak nincsenek kedvezőtlen következményei. A változtatások közé értjük a javításokat is, amelyek már átestek az ellenőrző tesztelésen. Ezek a kedvezőtlen következmények hatással lehetnek az adott komponensre, ahol a javítást végeztük, más komponensekre a rendszeren belül vagy akár más kapcsolódó rendszerekre. A regressziós tesztelés nem feltétlenül korlátozódik magára a teszt tárgyára, lehetséges, hogy a tesztkörnyezet változása miatt szükséges a tesztelés. Annak érdekében, hogy optimalizálni lehessen a szükséges regressziós tesztelés mértékét, javasolt először egy hatáselemzés elvégzése. A hatáselemzés megmutatja, hogy a szoftver mely részei lehetnek érintettek a módosítás által.

A regressziós tesztkészletek számos alkalommal futnak és általánosságban a regressziós tesztek száma növekedik minden iterációval vagy kiadással, ezért remek választás ezeket a teszteket automatizálni. Ezen tesztek automatizációját a projekt korai szakaszában ajánlatos elkezdeni. Ahol folyamatos integrációt használnak, például DevOps esetén, ott jó gyakorlat az automatizált regressziós tesztek alkalmazása. Ezért, a szituációtól függően, regressziós tesztelés akár különböző tesztszinteken is alkalmazható.

Az ellenőrző tesztelés és/vagy a regressziós tesztelés szükséges minden tesztszinten, ha hibák kerülnek kijavításra és/vagy változtatások történnek ezeken a tesztszinteken.
2. Minta- és tesztrendszerek összeállítása, telepítése, konfigurálása
Windows rendszergazdai ismeretek: Telepítés, partíciókezelés (Win + R → diskmgmt.msc), hálózati beállítások, szolgáltatások kezelése.
Alap Linux: Parancssori alapok (cd, ls, cp, chmod, ps, systemctl, ifconfig, clear, pwd)
cd – könyvtárváltás
Belép egy másik mappába.
cd Dokumentumok
cd /home/felhasznalo/Asztal
cd .. – eggyel visszalép (szülőmappába).
clear és pwd – alapok
clear - képernyő törlése
pwd - aktuális könyvtár megjelenítése
ls – fájlok és mappák listázása
Kilistázza az aktuális könyvtár tartalmát. A - után érzékeny a kis és nagy betűkre.
ls – egyszerű lista
ls -l – részletes (méret, jogosultság, dátum)
ls -a – rejtett fájlokat is mutatja
ls -la – részletes (méret, jogosultság, dátum) és a rejtett fájlokat is mutatja
ls -R – listázza az aktuális könyvtár tartalmát és minden almappát is — rekurzívan, azaz „belülről kifelé” végigmegy minden könyvtáron
ls -laR – részletes (méret, jogosultság, dátum) és a rejtett fájlokat is mutatja, listázza az aktuális könyvtár tartalmát és minden almappát is — rekurzívan, azaz „belülről kifelé” végigmegy minden könyvtáron.
mkdir – könyvtár (mappa) létrehozása
Új mappát hoz létre az aktuális könyvtárban.
mkdir tesztek – létrehoz egy "tesztek" nevű mappát.
mkdir /home/felhasznalo/projekt – létrehoz egy mappát a megadott elérési úton
mkdir -v ujmappa – a "-v" kapcsoló: tájékoztat, hogy létrejött-e a könyvtár (részletes kimenet).
cp – másolás
Fájlokat vagy mappákat másol.
cp fajl.txt /home/felhasznalo/Asztal
cp -r mappa /home/felhasznalo/ – mappát rekurzívan (tartalommal együtt).
chmod – jogosultságok módosítása
Átállítja, hogy ki olvashatja, írhatja vagy futtathatja a fájlt.
chmod 755 script.sh – tulajdonos futtathatja, mások csak olvashatják.
chmod +x script.sh – futtathatóvá teszi.
ps – folyamatok listázása
Megmutatja a futó programokat (processzeket).
ps – egyszerű lista
ps aux – minden folyamat részletesen.
systemctl – szolgáltatások kezelése
Elindít, leállít vagy újraindít rendszer-szolgáltatásokat (pl. webserver, adatbázis).
systemctl start apache2 – szolgáltatás indítása
systemctl stop apache2 – szolgáltatás leállítása
systemctl restart apache2 – újraindítás
systemctl status apache2 – állapot lekérdezése.
ifconfig – hálózati beállítások megtekintése
Megmutatja a számítógép hálózati interfészeinek (pl. Wi-Fi, Ethernet) IP-címét és beállításait.
ifconfig – hálózati interfészek állapota
enp0s3 – Ethernet (vezetékes) kártya
wlp2s0 – Wi-Fi kártya
lo – loopback (sajátgép, localhost)
ping 127.0.0.1 – sajátgép pinnelése
(Újabb rendszereken helyette: ip a)
route n – átjáró megjelenítése, ezen kommunikál a gépünk azokkal akik nincsenek vele egy hálózaton
arp -a – segítségével felderíteni a hálózaton lévő eszközöket
traceroute 8.8.8.8 – Windows-on tracert paranccsal segítségével meg tudjuk nézni, hogy a gépünk milyen útvonalon keresztül éri el a megadott IP-címet, és mennyi időbe telik az egyes útvonalpontok elérése. (8.8.8.8 -> dns.google)
Egyszerű szoftvertelepítés: apt, yum.
Virtualizáció: VirtualBox vagy VMware – készíts több virtuális gépet, hálózatot konfigurálj.
Android: Android eszköz csatlakoztatása, logok lekérése (Android Debug Bridge – ADB).
Diskpart parancssori eszköz
Ez egy haladó, parancssoros eszköz, amivel részletesen vezérelhetjük a lemezeket.

Elindítása: Futtatás rendszergazdaként: cmd → diskpart

Gyakori parancsok:
list disk – megjeleníti a lemezeket.
select disk X – kiválasztja az X számú lemezt.
list partition – a kiválasztott lemez partícióit listázza.
create partition primary size=10240 – új elsődleges partíció létrehozása (pl. 10 GB).
format fs=ntfs quick – NTFS formázás gyors módban.
assign letter=E – meghajtóbetűjel kiosztása.
delete partition – partíció törlése.
Előnye: Olyan műveletek is elérhetők vele, amiket a Lemezkezelő GUI nem enged (pl. MBR/GPT konverzió, teljes lemez törlése).

3. Forráskód módosítás, fordítás, linkelés
Programozási alapismeretek: Legalább C/C++ vagy C# alapszint (változók, vezérlési szerkezetek, függvények).
Build folyamat: Visual Studio használata (projektek megnyitása, fordítás).
GCC / Makefile alapok: Ha Linux oldalon kell dolgozni.
Verziókezelés: Git alapok (klónozás, commit, push/pull, branch).
4. Továbbfejlesztési javaslatok, együttműködés fejlesztőkkel
Kommunikáció: Hibák és ötletek világos, rövid összefoglalása (pl. „user story” formában).
Dokumentáció: Jegyzetek készítése, képernyőképek, jegyzőkönyvek.
Agilis módszertan: Ismerkedj a Scrum / Kanban alapjaival (pl. napi standup, backlog).
5. Rendszer bemutatása, oktatás
Prezentációkészítés: PowerPoint alapok, képernyőfelvételek, struktúrált oktatási anyagok készítése.
Előadói készségek: Próbálj ki magyarázni egyszerű feladatokat ismerősnek (tanuld meg érthetően átadni az infót).
6. Felhasználók támogatása
Távoli elérés: TeamViewer, RDP, AnyDesk – kapcsolatfelvétel és alap hibaelhárítás.
Ügyfélkommunikáció: Udvarias, lényegretörő emailírás; alap problémamegoldási forgatókönyvek.
7. Hálózati alapismeretek
IP-címzés, DHCP, DNS: Ismerd meg az alapokat (pl. hogyan ellenőrzöd ipconfig /all (Windows)/ifconfig (Linux) paranccsal).
Tesztelés hálózaton: ping, tracert, portellenőrzés (telnet, nc).
IP cím
Teljes nevén: Internet Protocol (szabványos azonosító)
Egyedi számsor, ami minden hálózatra csatlakozó eszközt azonosít (pl. számítógép, telefon, nyomtató).
Olyan, mint egy lakcím: ezen keresztül találják meg egymást az eszközök a hálózaton.
Két fajtája van:
IPv4: pl. 192.168.1.5 (32 bit, 4 db 0-255 közötti szám, oktet)
IPv6: hosszabb, 128 bit, 8 db 4-es blokkból áll (hextet)
Az IP cím logikai cím, ami változhat (pl. router újraindítás után).
Külső IP: What is my IP oldalon nézhető.
Belső IP: Windows parancssorban: ipconfig /all
Hogyan lehet IP címe egy gépnek?
Statikus IP: Kézzel állítod be a gépen.
DHCP szervertől kapja. (A szerver lehet egy router.)
Ha nincs a hálózaton DHCP, akkor kézzel kell megadni az IP címet.
Ha van DHCP, akkor a gép automatikusan kap egy IP címet, amikor csatlakozik a hálózathoz.
Alapvetően igyekszik ugyanannak a gépnek ugyanazt az IP címet adni, van memóriája, de ha az IP cím már foglalt, akkor másikat ad.
Mi az a netmaszk?
A netmaszk (vagy alhálózati maszk) egy 32 bites bitmaszk, amely IPv4-cím esetén megmutatja, hogy az adott IP cím hány bitje azonosítja a hálózatot és hány bit a gazdagépet.
A bitmaszk bináris formában egymás után következő 1-esekből (hálózati rész) és 0-ásokból (hoszt rész) áll. Például a 255.255.255.0 maszk binárisan 11111111.11111111.11111111.00000000 és jelöli a /24 címtartományt. Ha azonos a gépet netmaszkja, akkor látják egymást a hálózaton. Ha különböző switch-en vannak, akkor is látják egymást.


Subnet mask
MAC cím
Teljes nevén: Media Access Control cím
Fizikai azonosító, amit a hálózati kártya gyártásakor kap.
Egyedi az egész világon (mint egy sorozatszám): pl. 00:1A:2B:3C:4D:5E
A hálózaton belül segít eldönteni, melyik adatcsomag melyik eszközhöz menjen.
Általában nem változik (de vannak technikák a módosítására).
DHCP
Teljes nevén: Dynamic Host Configuration Protocol
Szolgáltatás/protokoll, ami automatikusan ad IP címet az eszközödnek.
Ha csatlakozol egy Wi-Fi-hez, nem kell kézzel beírnod az IP címet – a DHCP szerver kiosztja neked.
Egy router gyakran DHCP szerverként működik otthoni hálózatokban.
Nemcsak IP címet ad, hanem más beállításokat is: pl. alapértelmezett átjáró (gateway), DNS szerver címe.
Fogalmak röviden
Fogalom	Jelentés
IP cím	Egyedi hálózati cím, ami az eszközöket az interneten vagy helyi hálózaton azonosítja.
MAC cím	Egyedi hardverazonosító cím, amit a hálózati eszköz gyártásakor kap.
DHCP	Egy protokoll, ami automatikusan kiosztja az IP címeket és egyéb hálózati beállításokat.
Internet nélkül is működik a helyi hálózat?
Internet nem kell ahhoz, hogy számítógépek kommunikáljanak egymással egy helyi hálózaton (LAN) belül.
Hogyan köss össze 3 gépet internet nélkül?
Router / switch / hub használatával
Kell: 1 router vagy switch, Ethernet kábelek, 3 számítógép LAN kártyával
Lépések:
Minden gépet kábellel csatlakoztatsz a routerhez vagy switchhez.
A gépek automatikusan láthatják egymást (ha a tűzfal nem tiltja).
Ha van DHCP a routeren: kioszt IP-címeket.
Ha nincs DHCP: állíts be statikus IP-címet kézzel (pl. 192.168.1.2, 192.168.1.3, 192.168.1.4).
Közvetlen összekötés
Régen cross-over kábel kellett, ma már a legtöbb hálózati kártya automatikusan érzékeli.
3 géphez bonyolult, mert csak 2 gépet lehet közvetlenül összekötni egy kábellel.
Több géphez mindenképp kell egy switch vagy router!
Wi-Fi Ad-hoc
Egy gép létrehoz egy Wi-Fi hotspotot (Access Point), a másik 2 gép rácsatlakozik.
Ez is csak helyi kapcsolat, nincs internet.
Példa statikus IP-vel:
Gép 1 IP: 192.168.1.2
Gép 2 IP: 192.168.1.3
Gép 3 IP: 192.168.1.4
Alhálózati maszk: 255.255.255.0
Átjáró: hagyható üresen (nincs internet)
Mire jó?
Fájlmegosztás
Lokális játékok (LAN game)
Szerver–kliens tesztelés
Nyomtató megosztás
Összefoglaló táblázat
Kellék	Mit csinálj?
Switch/Router	Minden gépet kábellel csatlakoztass.
Ethernet kábel	3 géphez mindenképp switch/router kell.
Wi-Fi Ad-hoc	Egy gép hoz létre hotspotot, a többiek csatlakoznak.
IP-címek	Ha nincs DHCP, kézzel add meg a címeket.
Helyi hálózat (LAN) kialakítása (internet nélkül)
Mi az, hogy hálózat?
Egy hálózat (LAN) összeköti az eszközöket, hogy tudjanak egymással adatot cserélni (pl. fájlmegosztás, közös nyomtató, LAN játék, helyi szerver).
Miket kell hozzá kitalálni?
Milyen eszközök lesznek? (PC-k, laptopok, nyomtató stb.)
Hogy kötöd össze őket?
Vezetékes LAN: Ethernet kábellel (UTP) → routerhez vagy switchhez dugod az eszközöket.
Vezeték nélküli LAN (Wi-Fi): Egy router biztosítja a Wi-Fi-t vagy létrehozol egy Ad-hoc Wi-Fi hálózatot.
Kell IP-cím terv!
DHCP-vel: router automatikusan kiosztja.
Statikus IP-vel: kézzel állítod be (pl. 192.168.1.2 – 192.168.1.254)
Alhálózati maszk: 255.255.255.0
Átjáró: lehet üres (nincs internet)
Példa: 3 gépes LAN routerrel
PC1 ──┐
       │
PC2 ──┼─ Router/Switch ── (esetleg nyomtató)
       │
PC3 ──┘
          
Csatlakoztasd a gépeket kábellel a routerhez vagy switchhez.
Ellenőrizd, hogy ugyanabban a hálózatban vannak (pl. minden gép IP-je 192.168.1.x).
Engedélyezd a fájlmegosztást, ha szeretnél fájlokat átküldeni.
Próbáld ki: ping paranccsal ellenőrizd, látják-e egymást (pl. ping 192.168.1.3).
Wi-Fi-s megoldás
Egy gép is csinálhat hotspotot (Ad-hoc), a többiek erre csatlakoznak.
IP-cím kiosztás lehet automatikus (ha van DHCP szoftver) vagy manuális.
Tűzfal
Gyakori hiba: a Windows tűzfal vagy vírusirtó blokkolja a fájlmegosztást! Helyi hálózatnál engedélyezd a helyi forgalmat.
8. Szakmai angol
Angol technikai dokumentáció olvasása: (pl. Microsoft Docs, GitHub README).
Tesztelés közben: Angol nyelvű bugreport és changelog megértése.
9. Microsoft DevOps Server
Ingyenes verzió: Azure DevOps Server
9.1 Alapok
9.1.1 Mi az az Azure DevOps Server?
Egy Microsoft által fejlesztett eszköz, amivel a fejlesztőcsapatok meg tudják tervezni, fejleszteni, tesztelni és kiadni a szoftvereiket.

Régi nevén Team Foundation Server (TFS).

Cégek belső hálózatán is telepíthető (nem csak felhőben, mint az Azure DevOps Services).

9.1.2 Mire való?
Fő célja, hogy minden fejlesztési lépést egy helyen kezeljetek:

Tervezés – feladatok, hibajegyek, user story-k nyilvántartása.
Kódkezelés – verziókövetés Git vagy TFVC (Team Foundation Version Control) segítségével.
Automatizált build – a kód lefordítása, tesztek futtatása.
Release (kiadás) – a kész szoftver telepítése teszt vagy éles környezetbe.
Tesztelés – manuális és automatizált tesztek kezelése.
 Software development models

9.1.3 Fő részei (moduljai)
Azure Boards
Feladatkezelő rendszer.
Láthatod, ki mit csinál, milyen hibák vannak, hol tart a projekt.
Kanban-tábla vagy Scrum sprintek formájában.
Azure Repos
Kód tárolása és verziókezelése Git vagy TFVC segítségével.
Itt vannak a pull requestek, branchek, merge-ek.
Azure Pipelines
Automatizált folyamatok, amik a kódot:
Build-elik (lefordítják, csomagolják)
Tesztelik
Deploy-olják (telepítik)
CI/CD (Continuous Integration / Continuous Delivery) megvalósítására.
Azure Test Plans
Manuális és automatizált tesztek nyilvántartása, futtatása.
Tesztelési eredmények követése.
Azure Artifacts
Különböző csomagok (NuGet, npm, Maven stb.) tárolása és megosztása a csapaton belül.
9.1.4 Hogyan illeszkedik a munkába?
A projektvezető beírja a feladatokat a Boards-ba.
A fejlesztő a Repos-ban dolgozik a kódon, commitol, pushol.
A Pipelines automatikusan buildel és tesztel.
A sikeres build után Release Pipeline telepíti a kódot.
A tesztelők a Test Plans-ben rögzítik a hibákat, amiket visszadobnak a fejlesztőknek.

9.1.5 Miért jó?
Átlátható – mindenki látja, mi történik.
Automatizált – nem kell kézzel telepítgetni vagy fordítani.
Biztonságos – verziókezelés, jogosultságok, naplózás.
Rugalmas – kisebb és nagyobb csapatoknak is működik.

9.2 Alapfogalmak, kifejezések
A DevOps alapfogalmak és kulcselemek a következők:
Folyamatos integráció (CI): A fejlesztés során a kód változtatásait rendszeresen egy közös tárba integrálják, automatikus teszteléssel biztosítva a minőséget.
Folyamatos szállítás (Continuous Delivery, CD): Olyan folyamat, amely biztosítja, hogy a kód mindig telepíthető állapotban legyen, de a kiadás manuális jóváhagyáshoz kötött.
Folyamatos bevezetés (Continuous Deployment): A kódváltoztatások automatikus, kézi beavatkozás nélküli élesítését jelenti.
Infrastruktúra mint kód (Infrastructure as Code, IaC): Az IT infrastruktúra programozott, automatizált kezelése, mely biztosítja az állandóan azonos környezeteket fejlesztés és éles rendszer között.
Automatizálás: Az ismétlődő feladatok automatizálása a hibák minimalizálása és a gyorsabb kiadás érdekében.
Megfigyelés és naplózás: A rendszerek folyamatos figyelése a megfelelő működés és a gyors problémakezelés érdekében.
Együttműködés és kommunikáció: A fejlesztők, tesztelők és üzemeltetők szoros, folyamatos együttműködése a teljes szoftverfejlesztési életciklus során.
A DevOps életciklus jellemzően a következő fázisokat foglalja magában: tervezés, fejlesztés, integráció, tesztelés, bevezetés, megfigyelés és visszajelzés.
Előnyt adó extra dolgok (ha időd van):
Automatizált tesztelés: Pl. Selenium vagy Postman (API-teszt).
Microsoft DevOps Server: Feladatok, build pipeline-ok alapja.
Alap rádió/telekommunikációs fogalmak (ha a cég profilja érinti).

# Források

📄 ISTQB-CTFL Syllabus 4.0 (magyar, PDF)
📝 Saját jegyzetek, melyeket a Ruander junior szoftvertesztelői tanfolyamon készítettem.
▶️ YouTube: Hálózati alapismeretek playlist https://www.youtube.com/watch?v=x75rST1j2Oc&list=PLih210Tv6IOTG2SCA9W6zOPyE21k4t86a
▶️ YouTube: Linux parancssor alapok playlist https://www.youtube.com/watch?v=ZyQELacHYzU&list=PLX7PhJYdwFyD3q6J3LZhIz-Xx46ybBDvr
📄 DevOps állásinterjún kezdőknek feltett leggyakoribb kérdések https://nixstech.com/hu/hirek/devops-interjukerdesek-es-valaszok-kezdoknek/
📄 DevOps Alapjai Eszközkészlet Kezdőknek https://devopsakademia.com/course/devops-alapjai-eszkozkeszlet-kezdoknek/?order-complete=order-689ad3ed4e2ce
📄 The Transition to DevOps https://analyze.co.za/the-transition-to-devops/