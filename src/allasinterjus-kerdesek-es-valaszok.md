# Állásinterjús kérdések és válaszok – hálózat, programozás, SQL, OOP

# CV készítéshez

RX Resume https://rxresu.me/
Canva https://www.canva.com/hu_hu/
LinkedIn profil frissítése https://www.linkedin.com/

# Alapvető információk az álláskereséshez

- Az álláshirdetés nem egy **checklist**, hanem egy **wishlist**. A döntést bízd az interjúztatókra.
- Nem kell minden frameworköt, programozási nyelvet vagy új eszközt ismerned.
- Sokkal fontosabb, hogy stabil alapokkal rendelkezz.
- A problémamegoldó képesség és a tanulási hajlandóság gyakran többet számít, mint az, hogy minden követelményt kipipálj.

# IP cím

Teljes nevén: Internet Protocol (szabványos azonosító)
Egyedi számsor, ami minden hálózatra csatlakozó eszközt azonosít (pl. számítógép, telefon, nyomtató).
Olyan, mint egy lakcím: ezen keresztül találják meg egymást az eszközök a hálózaton.
Két fajtája van:
IPv4: pl. 192.168.1.5 (32 bit, 4 db 0-255 közötti szám, oktet)
IPv6: hosszabb, 128 bit, 8 db 4-es blokkból áll (hextet)
Az IP cím logikai cím, ami változhat (pl. router újraindítás után).
Külső IP: What is my IP oldalon nézhető. https://whatismyipaddress.com/
Belső IP: Windows parancssorban: ipconfig /all

# MAC cím

Teljes nevén: Media Access Control cím
Fizikai azonosító, amit a hálózati kártya gyártásakor kap.
Egyedi az egész világon (mint egy sorozatszám): pl. 00:1A:2B:3C:4D:5E
A hálózaton belül segít eldönteni, melyik adatcsomag melyik eszközhöz menjen.
Általában nem változik (de vannak technikák a módosítására).

# DHCP

Teljes nevén: Dynamic Host Configuration Protocol
Szolgáltatás/protokoll, ami automatikusan ad IP címet az eszközödnek.
Ha csatlakozol egy Wi-Fi-hez, nem kell kézzel beírnod az IP címet – a DHCP szerver kiosztja neked.
Egy router gyakran DHCP szerverként működik otthoni hálózatokban.
Nemcsak IP címet ad, hanem más beállításokat is: pl. alapértelmezett átjáró (gateway), DNS szerver címe.

# Fogalmak röviden

Fogalom	Jelentés
IP cím	Egyedi hálózati cím, ami az eszközöket az interneten vagy helyi hálózaton azonosítja.
MAC cím	Egyedi hardverazonosító cím, amit a hálózati eszköz gyártásakor kap.
DHCP	Egy protokoll, ami automatikusan kiosztja az IP címeket és egyéb hálózati beállításokat.
Internet nélkül is működik a helyi hálózat?
Internet nem kell ahhoz, hogy számítógépek kommunikáljanak egymással egy helyi hálózaton (LAN) belül.

# Hogyan köss össze 3 gépet internet nélkül?

## Router / switch / hub használatával

Kell: 1 router vagy switch, Ethernet kábelek, 3 számítógép LAN kártyával
Lépések:
Minden gépet kábellel csatlakoztatsz a routerhez vagy switchhez.
A gépek automatikusan láthatják egymást (ha a tűzfal nem tiltja).
Ha van DHCP a routeren: kioszt IP-címeket.
Ha nincs DHCP: állíts be statikus IP-címet kézzel (pl. 192.168.1.2, 192.168.1.3, 192.168.1.4).

## Közvetlen összekötés

Régen cross-over kábel kellett, ma már a legtöbb hálózati kártya automatikusan érzékeli.
3 géphez bonyolult, mert csak 2 gépet lehet közvetlenül összekötni egy kábellel.
Több géphez mindenképp kell egy switch vagy router!

## Wi-Fi Ad-hoc

Egy gép létrehoz egy Wi-Fi hotspotot (Access Point), a másik 2 gép rácsatlakozik.
Ez is csak helyi kapcsolat, nincs internet.

# Példa statikus IP-vel:

Gép 1 IP: 192.168.1.2
Gép 2 IP: 192.168.1.3
Gép 3 IP: 192.168.1.4
Alhálózati maszk: 255.255.255.0
Átjáró: hagyható üresen (nincs internet)

## Mire jó?

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
Hogyan kötöd össze a weboldaladat egy SQL Serverrel?
Alapgondolat
A weboldalad (front-end + back-end) nem közvetlenül kapcsolódik az adatbázishoz, hanem a szerveroldali kód (back-end) kapcsolódik.
Backend létrehozza a kapcsolatot az SQL Serverhez
Futtatja a lekérdezéseket (SQL)
Visszaadja az adatokat a weboldalnak (általában JSON-ban)
Általános lépések
SQL Server beállítása
Telepítve van az SQL Server (pl. MSSQL Express)
Létrehozol egy adatbázist, táblákat
Biztosítasz egy felhasználót (pl. SQL Server Authentication vagy Windows Auth)
Megjegyzed a Connection String-et:
Server=localhost;Database=mydb;User Id=myuser;Password=mypassword;
Backend oldali nyelv / framework
Node.js → mssql csomag
.NET → SqlConnection
Python → pyodbc vagy SQLAlchemy
PHP, Java stb.
Kapcsolódás és lekérdezés (példa C# .NET):
using System.Data.SqlClient;

string connectionString = "Server=localhost;Database=MyDB;User Id=myuser;Password=mypassword;";

using (SqlConnection connection = new SqlConnection(connectionString))
{
    connection.Open();
    string sql = "SELECT * FROM Users";
    SqlCommand command = new SqlCommand(sql, connection);

    SqlDataReader reader = command.ExecuteReader();
    while (reader.Read())
    {
        Console.WriteLine(reader["Name"].ToString());
    }
}
              
Adatok visszaadása a front-endnek
A back-end API-t szolgáltat, pl. /api/users
Ez JSON-t küld vissza a böngészőnek
A front-end AJAX kéréssel lekéri:
fetch('/api/users')
  .then(res => res.json())
  .then(data => console.log(data));
              
Összefoglalva
Frontend (weboldal): kérést küld (HTTP)
Backend (szerveroldali kód): SQL Server-hez csatlakozik
SQL Server: válaszol a lekérdezésre
Backend: visszaküldi JSON-ban
Frontend: megjeleníti
Biztonsági szempontok
Soha ne tedd ki közvetlenül az adatbázist internetre!
Soha ne engedd, hogy a böngésző közvetlenül kapcsolódjon SQL Serverhez – mindig legyen köztes szerveroldali kód.
Használj prepared statementet vagy ORM-et az SQL injection ellen.
Röviden
Backend nyelv + Connection String + SQL driver + API réteg.
Mi az ORM?
ORM = Object-Relational Mapping – Programozási technika, amivel objektum-orientált nyelvek (Java, C#, Python, PHP, Ruby stb.) táblákhoz kapcsolódnak.
Az ORM réteg gondoskodik arról, hogy adatbázis táblák és a programbeli osztályok között legyen kapcsolat.
Példa: Adatbázis tábla: users → a kódban: User osztály, a sorok User objektumok.
Miért jó az ORM?
Nem kell kézzel SQL-t írnod minden CRUD művelethez.
Biztonságosabb (SQL injection elleni védelem beépítve).
Könnyebben karbantartható, újrahasznosítható kód.
Platformfüggetlen.
ORM példák SQL Server-hez
Platform	Példa ORM
.NET	Entity Framework, Dapper
Java	Hibernate, JPA
Python	SQLAlchemy, Django ORM
PHP	Doctrine, Eloquent (Laravel ORM)
Ruby	ActiveRecord (Ruby on Rails)
Mi az OOP?
Az objektum-orientált programozás (OOP, Object-Oriented Programming) egy programozási szemlélet, ahol a program objektumokból épül fel, amelyek a valós világ dolgait modellezik adattal és viselkedéssel együtt.
Kulcsfogalmak:
Objektum (Object): Egy konkrét példány, ami adatokat (attribútumok, property-k) és műveleteket (metódusok) tartalmaz.
Osztály (Class): Egy sablon, ami meghatározza, hogy az objektum milyen tulajdonságokkal és viselkedéssel rendelkezik.
Attribútum (Tulajdonság): Az objektum adatai (pl. név, kor, fajta).
Metódus (Művelet): Az objektum viselkedése, amit végre tud hajtani (pl. ugat(), eszik()).
OOP 4 fő alapelve:
Encapsulation (Adat elrejtés): Az adatok és a hozzájuk tartozó műveletek egy egységben (osztályban) vannak.
Inheritance (Öröklődés): Egy osztály örökölhet egy másik osztályból, így kódot lehet újrahasználni.
Polymorphism (Polimorfizmus): Ugyanaz a művelet többféleképpen viselkedhet.
Abstraction (Absztrakció): Csak a lényeges dolgokat mutatja meg, a részleteket elrejti.
Linkelés és fordítás
Fordítás (Compilation)
A fordítóprogram (compiler) átalakítja az általad írt forráskódot gép által érthető gépi kódra vagy egy köztes nyelvre (bytecode).
Példák:
C/C++: .c → .o (object file)
Java: .java → .class (bytecode)
Szintaktikai ellenőrzés, szimbolikus átalakítás, optimalizálás.
Linkelés (Linking)
A linker (összekötő program) összeilleszti a fordított object fájlokat és a külső könyvtárakat, hogy létrejöjjön egy futtatható állomány.
Példa: több fájlod van (main.o, utils.o), a linker mindent „összeragaszt” → program.exe
A fordítás csak lefordítja a kódot gépi utasításokra, de a külső függőségeket még nem rendezi el. A linker gondoskodik arról, hogy minden függvény, változó helye egyértelmű legyen a végleges programban.
Mi az Entity?
Egy entitás (entity) egy valós világban létező dolgot jelöl, amit az alkalmazásban modellezünk (pl. Felhasználó, Termék, Megrendelés).
OOP szempontból: egy entitás gyakran egy osztály példánya, amely tartalmazza az adatokat (attribútumok) és a hozzájuk kapcsolódó viselkedést (metódusok).
Adatbázis szempontból: egy entitás megfeleltethető egy adatbázis-táblának, ahol minden sor egy-egy entitás példány.
ORM-ben: az „entity” az adatbázis-tábla leképezése egy objektumra, amit a kódodban használsz.
JavaScript típusossága
Dynamically typed: A változók nem kötöttek egy adott típushoz, futás közben változhatnak.
Weakly typed: JavaScript automatikusan konvertálja az adattípusokat (type coercion).
Példa:
let valtozo = 42; // Number
valtozo = "szöveg"; // String
valtozo = true; // Boolean
Példa:
console.log("5" + 1); // "51"
console.log("5" - 1); // 4
console.log(true + 1); // 2
Tulajdonság	JavaScript-ben
Típusosság	Dinamikus, gyengén típusos
Változó típusa	Nem kötött, futás közben változhat
Típuskényszerítés	Automatikus, sokszor implicit
Előnyök: Rugalmas, gyors prototípus fejlesztéshez.
Hátrányok: Könnyebben fordulhatnak elő típushibák, nehezebb hibát találni.
Ha erősebb típusosságot szeretnél JS-ben: Használj TypeScript-et!
JS adattípusok
1) Primitív típusok
Típus	Példa
Number	42, 3.14, -7
String	"Helló", 'ChatGPT'
Boolean	true, false
Null	null
Undefined	undefined
BigInt	12345678901234567890n
Symbol	Symbol("egyedi")
Érték szerint tárolódnak, nem módosíthatók (immutable).
2) Objektum típusok
Object: const ember = { nev: "Anna", kor: 25 };
Array (Tömb): const lista = [1, 2, 3, 4];
Function: function hello() { console.log("Helló!"); }
Date: const datum = new Date();
RegExp: const regex = /[A-Z]+/g;
Map, Set: const map = new Map(); const set = new Set();
Error: throw new Error("Hiba történt!");
Primitív típus	Objektum típus
Tárolás	Érték szerint	Hivatkozás szerint
Módosítás	Nem lehet	Lehet property-ket módosítani
Példa	42	{ nev: "Anna" }
JavaScript-ben minden, ami nem primitív, az objektum! Még a tömb (Array) és a függvény (Function) is!
Az interjú végén
Az interjú végén kérdezd meg, hogy hány körös szokott lenni. Milyen előre lépési lehetőséget vannak. Mekkora a fluktuáció. Miért keresnek új kollégát. Mi történt az előzővel.

Valamit mindenféleképpen kérdezz!
