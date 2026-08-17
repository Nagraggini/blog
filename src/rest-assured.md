# Tartalomjegyzék

- [Tartalomjegyzék](#tartalomjegyzék)
- [Rest Assured alapjai (REST API tesztelés)](#rest-assured-alapjai-rest-api-tesztelés)
- [Projekt létrehozása](#projekt-létrehozása)
	- [pom.xml](#pomxml)
	- [BaseApiTest osztály](#baseapitest-osztály)
	- [CI bekapcsolása](#ci-bekapcsolása)
	- [Gitignore](#gitignore)
- [Maven wrapper beállítása és használata](#maven-wrapper-beállítása-és-használata)
	- [Teszt osztályok létrehozása](#teszt-osztályok-létrehozása)
	- [REST API tesztek röviden](#rest-api-tesztek-röviden)
- [Logolások](#logolások)
	- [Loggolás használata](#loggolás-használata)
- [POJO](#pojo)
	- [A REST Assured kérés felépítése](#a-rest-assured-kérés-felépítése)
- [`given()`](#given)
- [`when()`](#when)
- [`then()`](#then)
- [`extract()`](#extract)
- [`Response`](#response)
- [Gyakori HTTP státuszkódok](#gyakori-http-státuszkódok)
- [Legfontosabb importok](#legfontosabb-importok)
	- [Hamcrest Matcherek Rest Assured-ben](#hamcrest-matcherek-rest-assured-ben)
	- [Leggyakrabban használtak](#leggyakrabban-használtak)


# Rest Assured alapjai (REST API tesztelés)

[REST Assured Beginner Tutorial](https://www.youtube.com/watch?v=vgMyJhrMV0o&list=PLhW3qG5bs-L8xPrBwDv66cTMlFNeUPdJx&index=5)

REST API-s projektjeim magyarázatokkal:
- [petstore](https://github.com/Nagraggini/petstore) 
- [reqres](https://github.com/Nagraggini/reqres) 
- [jsonplaceholder-demo-api](https://github.com/Nagraggini/jsonplaceholder-demo-api)

API-tesztekkel a szerződés ellenőrzését végezzük el, vagyis a segítségükkel ellenőrizhetjük többek között a végpontok működését, a státuszkódokat, a válasz törzsét, a fejléceket, a válaszidőt, az üzleti szabályokat és az API-szerződés betartását. 

# Projekt létrehozása

Fájl -> new project -> maven -> create a simple project -> next 
group id: hu.tanulas
artifact id: proba -> Finish 

Jobb klikk a projekt mappán -> Build path -> Configure build path -> JRE System Library 21 legyen Utána bal oldalt kattints a Java Compiler-re és java 21-et állítsd be. Apply and close 

**A pom.xml-be az első sor végén lévő http-t írd át https-re!**

És ezt másold be:

```xml
	  <dependencies>
	 
		  <!-- Source: https://mvnrepository.com/artifact/io.rest-assured/rest-assured -->
		<dependency>
		    <groupId>io.rest-assured</groupId>
		    <artifactId>rest-assured</artifactId>
		    <version>5.5.6</version>
		    <scope>test</scope>
		</dependency>
		
	  </dependencies>
```

## pom.xml

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="https://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>hu.tanulas</groupId>
  <artifactId>proba</artifactId>
  <version>0.0.1-SNAPSHOT</version>
  
  
	  <dependencies>
	  
		  <!-- Source: https://mvnrepository.com/artifact/io.rest-assured/rest-assured -->
		<dependency>
		    <groupId>io.rest-assured</groupId>
		    <artifactId>rest-assured</artifactId>
		    <version>5.5.6</version>
		    <scope>test</scope>
		</dependency>
		
		<!-- JUnit 5 tesztkeretrendszer -->
		<!-- Source: https://mvnrepository.com/artifact/org.junit.jupiter/junit-jupiter -->
		<dependency>
		    <groupId>org.junit.jupiter</groupId>
		    <artifactId>junit-jupiter</artifactId>
		    <version>5.11.0</version>
		    <scope>test</scope>
		</dependency>
		
		<!-- Source: https://mvnrepository.com/artifact/org.apache.logging.log4j/log4j-core -->
		<dependency>
		    <groupId>org.apache.logging.log4j</groupId>
		    <artifactId>log4j-core</artifactId>
		    <version>2.26.0</version>
		    <scope>compile</scope>
		</dependency>
	
		<!--A response válaszokból esetleges objektumképzéshez szükség van json feldolgozó importra is, pl.: jackson -->
		<!-- JSON és Java objektumok közötti szerializációhoz/deszerializációhoz -->
		<!-- Source: https://mvnrepository.com/artifact/com.fasterxml.jackson.core/jackson-core -->
		<dependency>
		    <groupId>com.fasterxml.jackson.core</groupId>
		    <artifactId>jackson-databind</artifactId>
		    <version>2.17.1</version>
		    <scope>compile</scope>
		</dependency>

	  </dependencies>
	  
	  <!--Verzió megadása, de nem kötelező ezeknél is működik. Ezzel még biztosabb lesz a program.-->
	  <properties>
	  	<project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
	  	<maven.compiler.release>21</maven.compiler.release>
	  	<maven.compiler.target>21</maven.compiler.target>
	  </properties>
	  
	  
	  <build>
	    <plugins>
	        <plugin>
	            <groupId>org.apache.maven.plugins</groupId>
	            <artifactId>maven-surefire-plugin</artifactId>
	            <version>3.5.4</version>	         
	        </plugin>
	        
	        <plugin>
	            <groupId>org.apache.maven.plugins</groupId>
	            <artifactId>maven-compiler-plugin</artifactId>
	            <version>3.12.1</version>	
	            <configuration>      
	            	<release>21</release>
	            </configuration>     
	        </plugin>
	        <!--Utána navigálj el a cmd-ben a projekt mappáig, ahol a pom.xml van.
	        Aztán mvn clean test
	        -->
	    </plugins>
	</build>

	  
</project>
```

## BaseApiTest osztály

A base package-be rakd és innen származtasd a többit teszt osztályt.

```java
package api.base;

import org.junit.jupiter.api.BeforeEach;

import io.restassured.RestAssured;
import io.restassured.http.ContentType;

public class BaseApiTest {

	@BeforeEach
	protected void setup() {
        // Tesztelni kívánt weboldal címe.
		RestAssured.baseURI="https://jsonplaceholder.typicode.com/";
		
		RestAssured.requestSpecification=RestAssured
				.given()
					.accept(ContentType.JSON) // json formátumú választ várunk 
					.contentType(ContentType.JSON); // json formátumban küldjük a kérést
	}
}
```

## CI bekapcsolása

.github/workflows/maven-tests.yml

```yml
name: Run Rest Assured API Tests

on:
  push:
  pull_request:
  workflow_dispatch:

jobs:
  tests:
    runs-on: ubuntu-latest
    
    steps:
      - name: Checkout repository
        uses: actions/checkout@v4
        
      - name: Set up JDK21
        uses: actions/setup-java@v4
        with:
          distribution: 'temurin'
          java-version: '21'

	  - name: Make Maven Wrapper executable
		run: chmod +x mvnw

      - name: Run Maven Tests
        run: mvn -B clean test -DCI=true
    
      - name: Upload surefire test reports
        uses: actions/upload-artifact@v4
        with:
          name: surefire-reports
          path: target/surefire-reports
```

## Gitignore

```.gitignore
# =========================
# Java compiled files
# =========================
*.class

# =========================
# Maven
# =========================
target/
pom.xml.tag
pom.xml.releaseBackup
pom.xml.versionsBackup
pom.xml.next
release.properties
dependency-reduced-pom.xml

# =========================
# IntelliJ IDEA
# =========================
.idea/
*.iml
out/

# =========================
# Eclipse
# =========================
.project
.classpath
.settings/
.metadata/
bin/

# =========================
# VS Code
# =========================
.vscode/

# =========================
# OS files
# =========================
.DS_Store
Thumbs.db

# =========================
# Logs
# =========================
*.log

# =========================
# Selenium / test outputs
# =========================
screenshots/
reports/
allure-results/
allure-report/

# =========================
# Sonar
# =========================
.scannerwork/
.sonar/

# =========================
# Coverage
# =========================
coverage/
jacoco.exec

# =========================
# Temporary files
# =========================
*.tmp
*.temp
*.swp

# =========================
# Secrets and env, config.properties
# =========================
.env
.secrets
config.properties
```

# Maven wrapper beállítása és használata

A terminálban navigálj el a projekt mappájáig (pl.: cd GitHub/saucedemo) 
`mvn -v` 
Ezzel lecsekkoljuk, hogy van-e a gépen maven, ha nem ír verziót, a Mavent telepíteni kell: 
https://maven.apache.org/download.cgi 

pl. apache-maven-3.9.16-bin.zip letöltés, kicsomagolás 
környezeti változókhoz felvenni a bin mappáját

Linux-on még ez is kell egyszer: sudo apt install maven

Utána ezt futtasd: `mvn clean test`

Ezután jöhet a csomagolás: `mvn wrapper:wrapper` Ezután létrejönnek ezek: mvnw és mvnw.cmd fájlok és .mvn mappa. Innentől kezdve nem mvn utasítást kell használni, hanem mvnw utasítást! Ezután nem gond, ha nincsen maven a gépen telepítve, simán lehet terminálból is futtatni a projektet.

Futtatás linux-on: 
`./mvnw clean test`

win-on: 
`mvnw clean test`

## Teszt osztályok létrehozása

Minden package-t az src/test/java-ban hozz létre. Az api package-n belül pl.: api.UserList -> JUnit Test Case, csekkold, hogy tuti a Jupiter van felül kijelölve. 

## REST API tesztek röviden

A body vizsgálatoknál két paraméter határozza meg az elvárt eredmény ellenőrzését:

1. paraméter - meghatározza az adatot, amire az ellenőrzés vonatkozik
Ez egy json Path 
https://github.com/rest-assured/rest-assured/wiki/Usage#complex-json-paths		
							
2. paraméter - Hamcrest matcher, ezen keresztül mondjuk meg, hogy mit várunk el az adattal kapcsolatban. Rengeteg matcher létezik, pl.: nullValue, notNullValue, greaterThan, lessThan, equalTo, hasItem, anEmptyMap 
stb.:
https://hamcrest.org/JavaHamcrest/javadoc/2.2/org/hamcrest/Matchers.html

Lentebb lesz külön részletezve.

# Logolások

Surefire report: A teszt eredményét foglalja össze. Futás utáni összegzés.

Log: A hibakeresést segíti. 
[.then után -> .log().ifValidationFails() // A jó log, csak baj esetén szól (ha pl.: létező id-t adunk meg)]

Futás közbeni összegzés. 

## Loggolás használata

```java
package api.usersUpdate;

import static io.restassured.RestAssured.given;
import static org.hamcrest.Matchers.equalTo;

import org.apache.logging.log4j.LogManager;
import  org.apache.logging.log4j.Logger;

import org.junit.jupiter.api.Test;

import api.base.BaseApiTest;
import io.restassured.http.ContentType;

class UserUpdateTest extends BaseApiTest {

	//import org.apache.logging.log4j.Logger; 
	//A végén lévő zárójelben magát az osztályt kell megadni. 
	private static final Logger LOG=LogManager.getLogger(UserUpdateTest.class);
			
	@Test
	void userUpdateTestWithLog() {
		LOG.info("TC4.1 indítása, felhasználó módosítása");
		//Szövegblokk. Bemeneti adatok.
		String requestBody= """
				{	
					"name":"Teszt Elek",						
					"email":"tesztelek@teszt.com"
				}
				""";
		int userID=1;
		
		LOG.info("Módosítandó id: {} ",userID);
		
		//Kijelölöd a lento blokkot. Jobb klikk -> Surround with -> Try-catch Block
		try {
			//A restassured fluens api megoldást használ. 
			given()
				.contentType(ContentType.JSON)
				.body(requestBody)
			.when()	
				.put("/users/"+userID)
			.then()
				.log().ifValidationFails()
				.statusCode(200)
				.body("id", equalTo(1))
				.body("name", equalTo("Teszt Elek"))
				.body("email", equalTo("tesztelek@teszt.com"));
			
			LOG.info("TC4.1 sikeresen lefutott");
		} catch (Exception e) {
			LOG.error("Hiba történt a teszt futtatása közben: ",e);
			throw e;
		}
	}
}

```

Az src/test/resources/log4j2.xml fájlba:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<Configuration status="WARN"> <!-- Log4j-nek a belső működésére vonatkozik.  -->

    <Appenders>
    <!-- A konzolra írja ki a szöveget. -->
        <Console name="Console" target="SYSTEM_OUT">
        <!-- Megjelenítési forma.  -->
            <PatternLayout
                pattern="%d{HH:mm:ss} %-5level %logger - %msg%n"/>
        </Console>
    </Appenders>

    <Loggers>
        <Root level="INFO"> <!-- INFO szintől felfelé kerül megjelenítésre a loggolás. -->
            <AppenderRef ref="Console"/>
        </Root>
    </Loggers>

</Configuration>
```

# POJO

Külön package-et hozunk létre a POJO osztályok számára, amelyekben az objektumokat tároljuk.

A POJO (Plain Old Java Object) egyszerű Java osztály, amely általában csak adatokat tartalmaz, például mezőket, gettereket és settereket. Az elkülönített package segít a kód áttekinthetőségében és rendszerezésében.

Jackson-deszerializáció esetén a POJO-nak általában szüksége van paraméter nélküli konstruktorra, valamint írható propertykre, például setterekre.

Így néz ki egy osztálya:

```java
package userPOJO;

import com.fasterxml.jackson.annotation.JsonIgnoreProperties;

//Csak azokat a mezőket veszi figyelembe, 
//amiket az osztály adattagjaiként létrehozunk.
@JsonIgnoreProperties(ignoreUnknown=true)
public class User {
	
	private int id;
	private String name;
	private String username;
	private String email;
	
	public int getId() {
		return id;
	}
	public String getName() {
		return name;
	}
	public String getUsername() {
		return username;
	}
	public String getEmail() {
		return email;
	}
	
	 // A többi getter és setter...
}
```

## A REST Assured kérés felépítése

Importja: `import static io.restassured.RestAssured.*;`

```java
given()
    .header(...)
    .contentType(ContentType.JSON)
    .body(requestBody)

.when()
    .post("/users")

.then()
    .statusCode(201)
    .body("name", equalTo("John"));
```

---

# `given()`

A kérés előkészítése.

| Metódus                     | Mire való?                              | Példa                                      |
| --------------------------- | --------------------------------------- | ------------------------------------------ |
| `header()`                  | HTTP fejléc hozzáadása                  | `.header("Authorization", "Bearer token")` |
| `headers()`                 | Több fejléc egyszerre                   | `.headers("Accept", "application/json")`   |
| `contentType()`             | Request Content-Type                    | `.contentType(ContentType.JSON)`           |
| `accept()`                  | Elfogadott válasz típusa                | `.accept(ContentType.JSON)`                |
| `body()`                    | Request Body                            | `.body(requestBody) OR .body(onePOJOObj)`                       |
| `queryParam()`              | Query paraméter                         | `.queryParam("page", 2)`                   |
| `pathParam()`               | Path paraméter                          | `.pathParam("id", 5)`                      |
| `formParam()`               | Form paraméter                          | `.formParam("username", "admin")`          |
| `cookie()`                  | Cookie küldése                          | `.cookie("sessionId", "abc123")`           |
| `auth()`                    | Hitelesítés                             | `.auth().basic("user", "pass")`            |
| `log().all()`               | Teljes kérés naplózása                  | `.log().all()`                             |
| `log().body()`              | Csak a body naplózása                   | `.log().body()`                            |
| `log().headers()`           | Csak a headerek naplózása               | `.log().headers()`                         |
| `log().ifValidationFails()` | Csak sikertelen validáció esetén naplóz | `.log().ifValidationFails()`               |

---

# `when()`

A HTTP kérés elküldése.

| Metódus     | Mire való?    | Példa                 |
| ----------- | ------------- | --------------------- |
| `get()`     | GET kérés     | `.get("/users")`      |
| `post()`    | POST kérés    | `.post("/users")`     |
| `put()`     | PUT kérés     | `.put("/users/2")`    |
| `patch()`   | PATCH kérés   | `.patch("/users/2")`  |
| `delete()`  | DELETE kérés  | `.delete("/users/2")` |
| `options()` | OPTIONS kérés | `.options("/users")`  |
| `head()`    | HEAD kérés    | `.head("/users")`     |

---

# `then()`

A válasz ellenőrzése.

| Metódus                     | Mire való?                              | Példa                             |
| --------------------------- | --------------------------------------- | --------------------------------- |
| `statusCode()`              | HTTP státuszkód ellenőrzése             | `.statusCode(200)`                |
| `statusLine()`              | HTTP státusz sor                        | `.statusLine("HTTP/1.1 200 OK")`  |
| `contentType()`             | Content-Type ellenőrzése                | `.contentType(ContentType.JSON)`  |
| `body()`                    | JSON mező ellenőrzése                   | `.body("name", equalTo("John"))`  |
| `header()`                  | Header ellenőrzése                      | `.header("Server", "cloudflare")` |
| `headers()`                 | Több header ellenőrzése                 | `.headers(...)`                   |
| `cookie()`                  | Cookie ellenőrzése                      | `.cookie("sessionId")`            |
| `time()`                    | Válaszidő ellenőrzése                   | `.time(lessThan(3000L))`          |
| `log().all()`               | Teljes válasz naplózása                 | `.log().all()`                    |
| `log().body()`              | Csak a body naplózása                   | `.log().body()`                   |
| `log().ifValidationFails()` | Csak sikertelen validáció esetén naplóz | `.log().ifValidationFails()`      |

---

# `extract()`

Az ellenőrzés után adatokat nyerhetsz ki.

| Metódus                | Mire való?               | Példa                        |
| ---------------------- | ------------------------ | ---------------------------- |
| `extract().response()` | Teljes Response objektum | `.extract().response()`      |
| `extract().path()`     | Egy mező kiolvasása      | `.extract().path("data.id")` |
| `extract().jsonPath()` | JsonPath objektum        | `.extract().jsonPath()`      |
| `extract().xmlPath()`  | XML válasz feldolgozása  | `.extract().xmlPath()`       |
| `extract().as()`       | POJO-vá alakítás         | `.extract().as(User.class)`  |

---

# `Response`

Importja: `import io.restassured.response.Response;`

| Metódus                  | Mire való?             | Példa                                              |
| ------------------------ | ---------------------- | ---------------------------------------            |
| `getStatusCode()`        | HTTP státuszkód        | `response.getStatusCode()`                         |
| `getStatusLine()`        | HTTP státusz sor       | `response.getStatusLine()`                         |
| `getBody().asString()`   | Body Stringként        | `response.getBody().asString()`                    |
| `jsonPath().getObject()` | Objektum kiolvasása    | `response.jsonPath().getObject("data",User.class)` |
| `jsonPath().getString()` | String kiolvasása      | `response.jsonPath().getString("name")`            |
| `jsonPath().getInt()`    | Integer kiolvasása     | `response.jsonPath().getInt("id")`                 |
| `jsonPath().getList()`   | Lista kiolvasása       | `response.jsonPath().getList("data")`              |
| `prettyPrint()`          | Formázott JSON kiírása | `response.prettyPrint()`                           |
| `time()`                 | Válaszidő              | `response.time()`                                  |

A `response.jsonPath().getObject("data",User.class)`-nél a "data" a mezőköz (JSONPath-kifejezés vagy elérési útvonal). 
A User.class a POJO osztályból jön.
Viszont a putnál a mezőköz ne legyen üres "";

Ha a teljes response body egyetlen objektumot tartalmaz, közvetlenül használható az `.extract().as(User.class)`. Ha az objektum egy beágyazott mezőben található, használható a `jsonPath().getObject()`.

Példák:

```java
	User user = response.as(User.class);

	User user = response.jsonPath()
        .getObject("data", User.class);

	// Lista esetén.
	List<Album> albums = response.jsonPath()
        .getList("", Album.class);

	// A lista első eleme.
	Album album = response.jsonPath()
        .getObject("[0]", Album.class);
```

```java
Album album=given().when().get("/albums/25").then().log().ifValidationFails()
		.statusCode(200).extract().jsonPath().getObject("",Album.class);

assertEquals(3,album.getUserId());
assertEquals(25,album.getId());
assertEquals("vero maxime id possimus sunt neque et consequatur",album.getTitle());	
```

Keresés és az alapján történő törlés: 
```java		
		String albumTitle = "quidem molestiae enim";
		
		Album album=
			given()	
				.queryParam("title", albumTitle)
			.when()
				.get("/albums")
			.then()
				.log().ifValidationFails()
				.statusCode(200)
				.body("$", not(empty()))
				.body("title",hasItem(album.getTitle()))
				.extract().jsonPath().getObject("[0]", Album.class);
		
		given()			
			.pathParam("id", album.getId())
		.when()
  			.delete("/albums/{id}")
		.then()
			.log().ifValidationFails()
			.statusCode(anyOf(is(200),is(204)))
			.body("$", anyOf(anEmptyMap(),nullValue()));		
```

---

# Gyakori HTTP státuszkódok

| Kód   | Jelentés               |
| ----- | ---------------------- |
| `200` | OK                     |
| `201` | Created                |
| `202` | Accepted               |
| `204` | No Content             |
| `400` | Bad Request            |
| `401` | Unauthorized           |
| `403` | Forbidden              |
| `404` | Not Found              |
| `405` | Method Not Allowed     |
| `409` | Conflict               |
| `415` | Unsupported Media Type |
| `422` | Unprocessable Entity   |
| `500` | Internal Server Error  |

---

# Legfontosabb importok

```java
import static io.restassured.RestAssured.given;
import static org.hamcrest.Matchers.*;

import io.restassured.http.ContentType;
import io.restassured.response.Response;
```

## Hamcrest Matcherek Rest Assured-ben

| Matcher                  | Mire való?                                 | Példa                                                    |
| ------------------------ | ------------------------------------------ | -------------------------------------------------------- |
| `equalTo()`              | Pontosan megegyezik                        | `.body("name", equalTo("Janet"))`                        |
| `not()`                  | Negálás                                    | `.body("name", not(equalTo("Peter")))`                   |
| `is()`                   | Olvashatóbb szintaxis                      | `.body("id", is(2))`                                     |
| `nullValue()`            | Az érték null                              | `.body("data", nullValue())`                             |
| `notNullValue()`         | Az érték nem null                          | `.body("id", notNullValue())`                            |
| `empty()`                | Üres lista vagy Map                        | `.body("data", empty())`                                 |
| `emptyString()`          | Üres String                                | `.body("name", emptyString())`                           |
| `hasSize()`              | Lista mérete                               | `.body("data", hasSize(6))`                              |
| `hasItem()`              | Tartalmaz egy elemet                       | `.body("data.email", hasItem("janet.weaver@reqres.in"))` |
| `hasItems()`             | Több elemet is tartalmaz                   | `.body("data.id", hasItems(1,2,3))`                      |
| `contains()`             | Pontosan ezek az elemek ebben a sorrendben | `.body("data.id", contains(1,2,3))`                      |
| `containsInAnyOrder()`   | Pontosan ezek az elemek, sorrend mindegy   | `.body("data.id", containsInAnyOrder(3,1,2))`            |
| `everyItem()`            | Minden elem megfelel                       | `.body("data.email", everyItem(containsString("@")))`    |
| `hasKey()`               | Map tartalmaz kulcsot                      | `.body("$", hasKey("data"))`                             |
| `hasValue()`             | Map tartalmaz értéket                      | `.body("$", hasValue(2))`                                |
| `containsString()`       | Tartalmaz egy szövegrészt                  | `.body("email", containsString("@"))`                    |
| `startsWith()`           | Szöveg ezzel kezdődik                      | `.body("email", startsWith("janet"))`                    |
| `endsWith()`             | Szöveg ezzel végződik                      | `.body("email", endsWith(".in"))`                        |
| `matchesPattern()`       | Regex alapján egyezik                      | `.body("email", matchesPattern(".*@reqres\\.in"))`       |
| `greaterThan()`          | Nagyobb mint                               | `.body("id", greaterThan(0))`                            |
| `greaterThanOrEqualTo()` | Nagyobb vagy egyenlő                       | `.body("page", greaterThanOrEqualTo(1))`                 |
| `lessThan()`             | Kisebb mint                                | `.body("id", lessThan(100))`                             |
| `lessThanOrEqualTo()`    | Kisebb vagy egyenlő                        | `.body("page", lessThanOrEqualTo(10))`                   |
| `closeTo()`              | Közel van egy számhoz                      | `.body("price", closeTo(10.0, 0.5))`                     |
| `instanceOf()`           | Adott típusú objektum                      | `.body("id", instanceOf(Integer.class))`                 |
| `sameInstance()`         | Ugyanaz az objektum                        | Ritkán használják Rest Assured-ben                       |
| `anyOf()`                | Legalább egy feltétel igaz                 | `.body("status", anyOf(is("active"), is("inactive")))`   |
| `allOf()`                | Minden feltétel igaz                       | `.body("id", allOf(greaterThan(0), lessThan(100)))`      |

## Leggyakrabban használtak

| Ellenőrzés                  | Matcher            |
| --------------------------- | ------------------ |
| Egyenlőség                  | `equalTo()`        |
| Nem egyenlő                 | `not(equalTo())`   |
| Nem null                    | `notNullValue()`   |
| Null                        | `nullValue()`      |
| Nem üres					  | `not(empty())`	   |
| Lista mérete                | `hasSize()`        |
| Lista tartalmaz elemet      | `hasItem()`        |
| Lista több elemet tartalmaz | `hasItems()`       |
| Minden elem megfelel        | `everyItem()`      |
| Szövegrész keresése         | `containsString()` |
| Ezzel kezdődik              | `startsWith()`     |
| Ezzel végződik              | `endsWith()`       |
| Regex ellenőrzés            | `matchesPattern()` |
| Nagyobb mint                | `greaterThan()`    |
| Kisebb mint                 | `lessThan()`       |
| Több feltétel egyszerre     | `allOf()`          |
| Több lehetőség közül egyik  | `anyOf()`          |

Mezők létezését, így kell ellenőrizni:
`everyItem(allOf(hasKey("id"),hasKey("password")))`

Nem üresek-e az id mezők:
`body("data.id", everyItem(notNullValue()));`

String esetén:
`body("data.password", everyItem(not(isEmptyString())));`

Nem üres (teljes body válasz, lista, tömb, map vagy string):  `not(empty())`

Null érték biztosabb ellenőrzése:
`.body("$", anyOf(anEmptyMap(), nullValue(), empty()))`

A lista legalább egy elemet tartalmaz:
`body("$.size()", greaterThan(0))`

Példa kód: 
```java
	given()
			.queryParam("userId", 7) // Filtering
		.when()
			.get("/albums")
		.then()
			.log().ifValidationFails()
			.statusCode(200)
			.body("$", instanceOf(List.class))
			.body("size()", equalTo(10))			
			.body("userId", everyItem(equalTo(7)));
```