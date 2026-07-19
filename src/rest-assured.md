# Rest Assured alapjai (REST API tesztelés)

[REST Assured Beginner Tutorial](https://www.youtube.com/watch?v=vgMyJhrMV0o&list=PLhW3qG5bs-L8xPrBwDv66cTMlFNeUPdJx&index=5)

[Itt](https://github.com/Nagraggini/petstore) találod a REST API-s projektemet, benne magyarázattal. 


## A REST Assured kérés felépítése

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
| `body()`                    | Request Body                            | `.body(requestBody)`                       |
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

| Metódus                  | Mire való?             | Példa                                   |
| ------------------------ | ---------------------- | --------------------------------------- |
| `getStatusCode()`        | HTTP státuszkód        | `response.getStatusCode()`              |
| `getStatusLine()`        | HTTP státusz sor       | `response.getStatusLine()`              |
| `getBody().asString()`   | Body Stringként        | `response.getBody().asString()`         |
| `jsonPath().getString()` | String kiolvasása      | `response.jsonPath().getString("name")` |
| `jsonPath().getInt()`    | Integer kiolvasása     | `response.jsonPath().getInt("id")`      |
| `jsonPath().getList()`   | Lista kiolvasása       | `response.jsonPath().getList("data")`   |
| `prettyPrint()`          | Formázott JSON kiírása | `response.prettyPrint()`                |
| `time()`                 | Válaszidő              | `response.time()`                       |

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