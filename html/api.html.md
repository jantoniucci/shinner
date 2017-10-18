---
title: Swagger Petstore v1.0.0
language_tabs:
  - shell: Shell
  - http: HTTP
  - javascript: JavaScript
  - javascript--nodejs: Node.JS
  - ruby: Ruby
  - python: Python
  - java: Java
  - csharp: 'C#'
  - php: PHP
toc_footers:
  - >-
    <a href="https://github.com/Rebilly/generator-openapi-repo">Find out how to
    create Github repo for your OpenAPI spec.</a>
includes:
  - ./examples/api_2.yaml
search: true
highlight_theme: darkula
---

# Swagger Petstore v1.0.0

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

This is a sample server Petstore server.
You can find out more about Swagger at
[http://swagger.io](http://swagger.io) or on [irc.freenode.net, #swagger](http://swagger.io/irc/).
For this sample, you can use the api key `special-key` to test the authorization filters.
# Introduction
This API is documented in **OpenAPI format** and is based on
[Petstore sample](http://petstore.swagger.io/) provided by [swagger.io](http://swagger.io) team.
It was **extended** to illustrate features of [generator-openapi-repo](https://github.com/Rebilly/generator-openapi-repo)
tool and [ReDoc](https://github.com/Rebilly/ReDoc) documentation. In addition to standard
OpenAPI syntax we use a few [vendor extensions](https://github.com/Rebilly/ReDoc/blob/master/docs/redoc-vendor-extensions.md).
# OpenAPI Specification
This API is documented in **OpenAPI format** and is based on
[Petstore sample](http://petstore.swagger.io/) provided by [swagger.io](http://swagger.io) team.
It was **extended** to illustrate features of [generator-openapi-repo](https://github.com/Rebilly/generator-openapi-repo)
tool and [ReDoc](https://github.com/Rebilly/ReDoc) documentation. In addition to standard
OpenAPI syntax we use a few [vendor extensions](https://github.com/Rebilly/ReDoc/blob/master/docs/redoc-vendor-extensions.md).
# Cross-Origin Resource Sharing
This API features Cross-Origin Resource Sharing (CORS) implemented in compliance with  [W3C spec](https://www.w3.org/TR/cors/).
And that allows cross-domain communication from the browser.
All responses have a wildcard same-origin which makes them completely public and accessible to everyone, including any code on any site.

Base URLs:

* <a href="http://petstore.swagger.io/v2">http://petstore.swagger.io/v2</a>

* <a href="https://petstore.swagger.io/v2">https://petstore.swagger.io/v2</a>


<a href="http://swagger.io/terms/">Terms of service</a>
Email: <a href="mailto:apiteam@swagger.io">Support</a> 
License: <a href="http://www.apache.org/licenses/LICENSE-2.0.html">Apache 2.0</a>

# Authentication



- oAuth2 authentication. 

    - Flow: implicit
    - Authorization URL = [http://petstore.swagger.io/api/oauth/dialog](http://petstore.swagger.io/api/oauth/dialog)

|Scope|Scope Description|
|---|---|
|write:pets|modify pets in your account|
|read:pets|read your pets|




* API Key
    - Parameter Name: **api_key**, in: header. 



# pet

Everything about your Pets

## addPet

> Code samples

```csharp
PetStore.v1.Pet pet = new PetStore.v1.Pet();
pet.setApiKey("your api key");
pet.petType = PetStore.v1.Pet.TYPE_DOG;
pet.name = "Rex";
// set other fields
PetStoreResponse response = pet.create();
if (response.statusCode == HttpStatusCode.Created)
{
  // Successfully created
}
else
{
  // Something wrong -- check response for errors
  Console.WriteLine(response.getRawResponse());
}

```
```php
$form = new \PetStore\Entities\Pet();
$form->setPetType("Dog");
$form->setName("Rex");
// set other fields
try {
    $pet = $client->pets()->create($form);
} catch (UnprocessableEntityException $e) {
    var_dump($e->getErrors());
}

```
`POST /pet`

*Add a new pet to the store*

Add new pet to the store inventory.

> Body parameter

```json
{
  "petType": "string",
  "id": 0,
  "category": {
    "id": 0,
    "name": "string"
  },
  "name": "Guru",
  "photoUrls": [
    "string"
  ],
  "tags": [
    {
      "id": 0,
      "name": "string"
    }
  ],
  "status": "available"
}
```
```xml
<?xml version="1.0" encoding="UTF-8" ?>
<Pet>
  <petType>string</petType>
  <id>0</id>
  <category>
    <id>0</id>
    <name>string</name>
  </category>
  <name>Guru</name>
  <photoUrls>string</photoUrls>
  <tags>
    <id>0</id>
    <name>string</name>
  </tags>
  <status>available</status>
</Pet>
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
body|body|[Pet](#schemapet)|true|Pet object that needs to be added to the store
» petType|body|string|false|Type of a pet
» id|body|Unknown|false|Pet ID
» category|body|Unknown|false|Categories this pet belongs to
»» id|body|Unknown|false|Category ID
»» name|body|string|false|Category name
» name|body|string|true|The name given to a pet
» status|body|string|false|Pet status in the store
» photoUrls|body|[string(url)]|false|The list of URL to a cute photos featuring pet
» tags|body|[[Tag](#schematag)]|false|Tags attached to the pet
»» id|body|Unknown|false|Tag ID
»» name|body|string|false|Tag name


#### Enumerated Values

|Parameter|Value|
|---|---|
» status|available|
» status|pending|
» status|sold|

### Responses

Status|Meaning|Description|Schema
---|---|---|---|
405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|Invalid input|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: write:pets read:pets )
</aside>

## updatePet

> Code samples

```php
$form = new \PetStore\Entities\Pet();
$form->setPetId(1);
$form->setPetType("Dog");
$form->setName("Rex");
// set other fields
try {
    $pet = $client->pets()->update($form);
} catch (UnprocessableEntityException $e) {
    var_dump($e->getErrors());
}

```
`PUT /pet`

*Update an existing pet*

> Body parameter

```json
{
  "petType": "string",
  "id": 0,
  "category": {
    "id": 0,
    "name": "string"
  },
  "name": "Guru",
  "photoUrls": [
    "string"
  ],
  "tags": [
    {
      "id": 0,
      "name": "string"
    }
  ],
  "status": "available"
}
```
```xml
<?xml version="1.0" encoding="UTF-8" ?>
<Pet>
  <petType>string</petType>
  <id>0</id>
  <category>
    <id>0</id>
    <name>string</name>
  </category>
  <name>Guru</name>
  <photoUrls>string</photoUrls>
  <tags>
    <id>0</id>
    <name>string</name>
  </tags>
  <status>available</status>
</Pet>
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
body|body|[Pet](#schemapet)|true|Pet object that needs to be added to the store
» petType|body|string|false|Type of a pet
» id|body|Unknown|false|Pet ID
» category|body|Unknown|false|Categories this pet belongs to
»» id|body|Unknown|false|Category ID
»» name|body|string|false|Category name
» name|body|string|true|The name given to a pet
» status|body|string|false|Pet status in the store
» photoUrls|body|[string(url)]|false|The list of URL to a cute photos featuring pet
» tags|body|[[Tag](#schematag)]|false|Tags attached to the pet
»» id|body|Unknown|false|Tag ID
»» name|body|string|false|Tag name


#### Enumerated Values

|Parameter|Value|
|---|---|
» status|available|
» status|pending|
» status|sold|

### Responses

Status|Meaning|Description|Schema
---|---|---|---|
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid ID supplied|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Pet not found|None
405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|Validation exception|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: write:pets read:pets )
</aside>

## getPetById

> Code samples

```shell
# You can also use wget
curl -X GET http://petstore.swagger.io/v2/pet/{petId} \
  -H 'Accept: application/xml'

```

```http
GET http://petstore.swagger.io/v2/pet/{petId} HTTP/1.1
Host: petstore.swagger.io

Accept: application/xml

```

```javascript
var headers = {
  'Accept':'application/xml'

};

$.ajax({
  url: 'http://petstore.swagger.io/v2/pet/{petId}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/xml'

};

fetch('http://petstore.swagger.io/v2/pet/{petId}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/xml'
}

result = RestClient.get 'http://petstore.swagger.io/v2/pet/{petId}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/xml'
}

r = requests.get('http://petstore.swagger.io/v2/pet/{petId}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("http://petstore.swagger.io/v2/pet/{petId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /pet/{petId}`

*Find pet by ID*

Returns a single pet

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
petId|path|integer(int64)|true|ID of pet to return


> Example responses

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<Pet>
  <petType>string</petType>
  <id>0</id>
  <category>
    <id>0</id>
    <name>string</name>
  </category>
  <name>Guru</name>
  <photoUrls>string</photoUrls>
  <tags>
    <id>0</id>
    <name>string</name>
  </tags>
  <status>available</status>
</Pet>
```
```json
{
  "petType": "string",
  "id": 0,
  "category": {
    "id": 0,
    "name": "string"
  },
  "name": "Guru",
  "photoUrls": [
    "string"
  ],
  "tags": [
    {
      "id": 0,
      "name": "string"
    }
  ],
  "status": "available"
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[Pet](#schemapet)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid ID supplied|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Pet not found|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## updatePetWithForm

> Code samples

```shell
# You can also use wget
curl -X POST http://petstore.swagger.io/v2/pet/{petId} \
  -H 'Content-Type: application/x-www-form-urlencoded'

```

```http
POST http://petstore.swagger.io/v2/pet/{petId} HTTP/1.1
Host: petstore.swagger.io
Content-Type: application/x-www-form-urlencoded

```

```javascript
var headers = {
  'Content-Type':'application/x-www-form-urlencoded'

};

$.ajax({
  url: 'http://petstore.swagger.io/v2/pet/{petId}',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "name": "string",
  "status": "string"
}';
const headers = {
  'Content-Type':'application/x-www-form-urlencoded'

};

fetch('http://petstore.swagger.io/v2/pet/{petId}',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/x-www-form-urlencoded'
}

result = RestClient.post 'http://petstore.swagger.io/v2/pet/{petId}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Content-Type': 'application/x-www-form-urlencoded'
}

r = requests.post('http://petstore.swagger.io/v2/pet/{petId}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("http://petstore.swagger.io/v2/pet/{petId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`POST /pet/{petId}`

*Updates a pet in the store with form data*

> Body parameter

```yaml
name: string
status: string

```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
petId|path|integer(int64)|true|ID of pet that needs to be updated
body|body|object|false|No description
» name|body|string|false|Updated name of the pet
» status|body|string|false|Updated status of the pet


### Responses

Status|Meaning|Description|Schema
---|---|---|---|
405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|Invalid input|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: write:pets read:pets )
</aside>

## deletePet

> Code samples

```shell
# You can also use wget
curl -X DELETE http://petstore.swagger.io/v2/pet/{petId} \
  -H 'api_key: string'

```

```http
DELETE http://petstore.swagger.io/v2/pet/{petId} HTTP/1.1
Host: petstore.swagger.io

api_key: string

```

```javascript
var headers = {
  'api_key':'string'

};

$.ajax({
  url: 'http://petstore.swagger.io/v2/pet/{petId}',
  method: 'delete',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'api_key':'string'

};

fetch('http://petstore.swagger.io/v2/pet/{petId}',
{
  method: 'DELETE',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'api_key' => 'string'
}

result = RestClient.delete 'http://petstore.swagger.io/v2/pet/{petId}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'api_key': 'string'
}

r = requests.delete('http://petstore.swagger.io/v2/pet/{petId}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("http://petstore.swagger.io/v2/pet/{petId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("DELETE");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`DELETE /pet/{petId}`

*Deletes a pet*

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
api_key|header|string|false|No description
petId|path|integer(int64)|true|Pet id to delete


### Responses

Status|Meaning|Description|Schema
---|---|---|---|
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid pet value|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: write:pets read:pets )
</aside>

## uploadFile

> Code samples

```shell
# You can also use wget
curl -X POST http://petstore.swagger.io/v2/pet/{petId}/uploadImage \
  -H 'Content-Type: application/octet-stream' \
  -H 'Accept: application/json'

```

```http
POST http://petstore.swagger.io/v2/pet/{petId}/uploadImage HTTP/1.1
Host: petstore.swagger.io
Content-Type: application/octet-stream
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/octet-stream',
  'Accept':'application/json'

};

$.ajax({
  url: 'http://petstore.swagger.io/v2/pet/{petId}/uploadImage',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = ''string'';
const headers = {
  'Content-Type':'application/octet-stream',
  'Accept':'application/json'

};

fetch('http://petstore.swagger.io/v2/pet/{petId}/uploadImage',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/octet-stream',
  'Accept' => 'application/json'
}

result = RestClient.post 'http://petstore.swagger.io/v2/pet/{petId}/uploadImage',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Content-Type': 'application/octet-stream',
  'Accept': 'application/json'
}

r = requests.post('http://petstore.swagger.io/v2/pet/{petId}/uploadImage', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("http://petstore.swagger.io/v2/pet/{petId}/uploadImage");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`POST /pet/{petId}/uploadImage`

*uploads an image*

> Body parameter

```yaml
string

```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
petId|path|integer(int64)|true|ID of pet to update
body|body|string(binary)|false|No description


> Example responses

```json
{
  "code": 0,
  "type": "string",
  "message": "string"
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[ApiResponse](#schemaapiresponse)

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: write:pets read:pets )
</aside>

## findPetsByStatus

> Code samples

```shell
# You can also use wget
curl -X GET http://petstore.swagger.io/v2/pet/findByStatus?status=... \
  -H 'Accept: application/xml'

```

```http
GET http://petstore.swagger.io/v2/pet/findByStatus?status=... HTTP/1.1
Host: petstore.swagger.io

Accept: application/xml

```

```javascript
var headers = {
  'Accept':'application/xml'

};

$.ajax({
  url: 'http://petstore.swagger.io/v2/pet/findByStatus',
  method: 'get',
  data: '?status=...',
  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/xml'

};

fetch('http://petstore.swagger.io/v2/pet/findByStatus?status=...',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/xml'
}

result = RestClient.get 'http://petstore.swagger.io/v2/pet/findByStatus',
  params: {
  'status' => 'array[string]'
}, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/xml'
}

r = requests.get('http://petstore.swagger.io/v2/pet/findByStatus', params={
  'status': [
  "available"
]
}, headers = headers)

print r.json()
```

```java
URL obj = new URL("http://petstore.swagger.io/v2/pet/findByStatus?status=...");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /pet/findByStatus`

*Finds Pets by status*

Multiple status values can be provided with comma seperated strings

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
status|query|array[string]|true|Status values that need to be considered for filter


#### Enumerated Values

|Parameter|Value|
|---|---|
status|available|
status|pending|
status|sold|

> Example responses

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<petType>string</petType>
<id>0</id>
<category>
  <id>0</id>
  <name>string</name>
</category>
<name>Guru</name>
<photoUrls>string</photoUrls>
<tags>
  <id>0</id>
  <name>string</name>
</tags>
<status>available</status>
```
```json
[
  {
    "petType": "string",
    "id": 0,
    "category": {
      "id": 0,
      "name": "string"
    },
    "name": "Guru",
    "photoUrls": [
      "string"
    ],
    "tags": [
      {
        "id": 0,
        "name": "string"
      }
    ],
    "status": "available"
  }
]
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|Inline
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid status value|None

### Response Schema

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
anonymous|[[Pet](#schemapet)]|false|No description
» petType|string|false|Type of a pet
» id|integer(int64)|false|Pet ID
» category|[Category](#schemacategory)|false|Categories this pet belongs to
»» id|integer(int64)|false|Category ID
»» name|string|false|Category name
» name|string|true|The name given to a pet
» status|string|false|Pet status in the store
» photoUrls|[string(url)]|false|The list of URL to a cute photos featuring pet
» tags|[[Tag](#schematag)]|false|Tags attached to the pet
»» id|integer(int64)|false|Tag ID
»» name|string|false|Tag name



<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: write:pets read:pets )
</aside>

## findPetsByTags

> Code samples

```shell
# You can also use wget
curl -X GET http://petstore.swagger.io/v2/pet/findByTags?tags=... \
  -H 'Accept: application/xml'

```

```http
GET http://petstore.swagger.io/v2/pet/findByTags?tags=... HTTP/1.1
Host: petstore.swagger.io

Accept: application/xml

```

```javascript
var headers = {
  'Accept':'application/xml'

};

$.ajax({
  url: 'http://petstore.swagger.io/v2/pet/findByTags',
  method: 'get',
  data: '?tags=...',
  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/xml'

};

fetch('http://petstore.swagger.io/v2/pet/findByTags?tags=...',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/xml'
}

result = RestClient.get 'http://petstore.swagger.io/v2/pet/findByTags',
  params: {
  'tags' => 'array[string]'
}, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/xml'
}

r = requests.get('http://petstore.swagger.io/v2/pet/findByTags', params={
  'tags': [
  "string"
]
}, headers = headers)

print r.json()
```

```java
URL obj = new URL("http://petstore.swagger.io/v2/pet/findByTags?tags=...");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /pet/findByTags`

*Finds Pets by tags*

Muliple tags can be provided with comma seperated strings. Use tag1, tag2, tag3 for testing.

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
tags|query|array[string]|true|Tags to filter by


> Example responses

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<petType>string</petType>
<id>0</id>
<category>
  <id>0</id>
  <name>string</name>
</category>
<name>Guru</name>
<photoUrls>string</photoUrls>
<tags>
  <id>0</id>
  <name>string</name>
</tags>
<status>available</status>
```
```json
[
  {
    "petType": "string",
    "id": 0,
    "category": {
      "id": 0,
      "name": "string"
    },
    "name": "Guru",
    "photoUrls": [
      "string"
    ],
    "tags": [
      {
        "id": 0,
        "name": "string"
      }
    ],
    "status": "available"
  }
]
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|Inline
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid tag value|None

### Response Schema

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
anonymous|[[Pet](#schemapet)]|false|No description
» petType|string|false|Type of a pet
» id|integer(int64)|false|Pet ID
» category|[Category](#schemacategory)|false|Categories this pet belongs to
»» id|integer(int64)|false|Category ID
»» name|string|false|Category name
» name|string|true|The name given to a pet
» status|string|false|Pet status in the store
» photoUrls|[string(url)]|false|The list of URL to a cute photos featuring pet
» tags|[[Tag](#schematag)]|false|Tags attached to the pet
»» id|integer(int64)|false|Tag ID
»» name|string|false|Tag name



<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: write:pets read:pets )
</aside>

# store

Access to Petstore orders

## getInventory

> Code samples

```shell
# You can also use wget
curl -X GET http://petstore.swagger.io/v2/store/inventory \
  -H 'Accept: application/json'

```

```http
GET http://petstore.swagger.io/v2/store/inventory HTTP/1.1
Host: petstore.swagger.io

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'http://petstore.swagger.io/v2/store/inventory',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('http://petstore.swagger.io/v2/store/inventory',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'http://petstore.swagger.io/v2/store/inventory',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('http://petstore.swagger.io/v2/store/inventory', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("http://petstore.swagger.io/v2/store/inventory");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /store/inventory`

*Returns pet inventories by status*

Returns a map of status codes to quantities

> Example responses

```json
{
  "property1": 0,
  "property2": 0
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|Inline

### Response Schema

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
additionalProperties|object|false|No description



<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
apiKey
</aside>

## placeOrder

> Code samples

```shell
# You can also use wget
curl -X POST http://petstore.swagger.io/v2/store/order \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/xml'

```

```http
POST http://petstore.swagger.io/v2/store/order HTTP/1.1
Host: petstore.swagger.io
Content-Type: application/json
Accept: application/xml

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/xml'

};

$.ajax({
  url: 'http://petstore.swagger.io/v2/store/order',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "id": 0,
  "petId": 0,
  "quantity": 1,
  "shipDate": "2017-10-09T08:59:09Z",
  "status": "placed",
  "complete": false
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/xml'

};

fetch('http://petstore.swagger.io/v2/store/order',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/xml'
}

result = RestClient.post 'http://petstore.swagger.io/v2/store/order',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/xml'
}

r = requests.post('http://petstore.swagger.io/v2/store/order', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("http://petstore.swagger.io/v2/store/order");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`POST /store/order`

*Place an order for a pet*

> Body parameter

```json
{
  "id": 0,
  "petId": 0,
  "quantity": 1,
  "shipDate": "2017-10-09T08:59:09Z",
  "status": "placed",
  "complete": false
}
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
body|body|[Order](#schemaorder)|true|order placed for purchasing the pet
» id|body|Unknown|false|Order ID
» petId|body|Unknown|false|Pet ID
» quantity|body|integer(int32)|false|No description
» shipDate|body|string(date-time)|false|Estimated ship date
» status|body|string|false|Order Status
» complete|body|boolean|false|Indicates whenever order was completed or not


#### Enumerated Values

|Parameter|Value|
|---|---|
» status|placed|
» status|approved|
» status|delivered|

> Example responses

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<Order>
  <id>0</id>
  <petId>0</petId>
  <quantity>1</quantity>
  <shipDate>2017-10-09T08:59:09Z</shipDate>
  <status>placed</status>
  <complete>false</complete>
</Order>
```
```json
{
  "id": 0,
  "petId": 0,
  "quantity": 1,
  "shipDate": "2017-10-09T08:59:09Z",
  "status": "placed",
  "complete": false
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[Order](#schemaorder)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid Order|None

<aside class="success">
This operation does not require authentication
</aside>

## getOrderById

> Code samples

```shell
# You can also use wget
curl -X GET http://petstore.swagger.io/v2/store/order/{orderId} \
  -H 'Accept: application/xml'

```

```http
GET http://petstore.swagger.io/v2/store/order/{orderId} HTTP/1.1
Host: petstore.swagger.io

Accept: application/xml

```

```javascript
var headers = {
  'Accept':'application/xml'

};

$.ajax({
  url: 'http://petstore.swagger.io/v2/store/order/{orderId}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/xml'

};

fetch('http://petstore.swagger.io/v2/store/order/{orderId}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/xml'
}

result = RestClient.get 'http://petstore.swagger.io/v2/store/order/{orderId}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/xml'
}

r = requests.get('http://petstore.swagger.io/v2/store/order/{orderId}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("http://petstore.swagger.io/v2/store/order/{orderId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /store/order/{orderId}`

*Find purchase order by ID*

For valid response try integer IDs with value <= 5 or > 10. Other values will generated exceptions

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
orderId|path|integer(int64)|true|ID of pet that needs to be fetched


> Example responses

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<Order>
  <id>0</id>
  <petId>0</petId>
  <quantity>1</quantity>
  <shipDate>2017-10-09T08:59:09Z</shipDate>
  <status>placed</status>
  <complete>false</complete>
</Order>
```
```json
{
  "id": 0,
  "petId": 0,
  "quantity": 1,
  "shipDate": "2017-10-09T08:59:09Z",
  "status": "placed",
  "complete": false
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[Order](#schemaorder)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid ID supplied|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Order not found|None

<aside class="success">
This operation does not require authentication
</aside>

## deleteOrder

> Code samples

```shell
# You can also use wget
curl -X DELETE http://petstore.swagger.io/v2/store/order/{orderId}

```

```http
DELETE http://petstore.swagger.io/v2/store/order/{orderId} HTTP/1.1
Host: petstore.swagger.io


```

```javascript

$.ajax({
  url: 'http://petstore.swagger.io/v2/store/order/{orderId}',
  method: 'delete',

  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

fetch('http://petstore.swagger.io/v2/store/order/{orderId}',
{
  method: 'DELETE'

})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'


result = RestClient.delete 'http://petstore.swagger.io/v2/store/order/{orderId}',
  params: {
  }

p JSON.parse(result)
```

```python
import requests

r = requests.delete('http://petstore.swagger.io/v2/store/order/{orderId}', params={

)

print r.json()
```

```java
URL obj = new URL("http://petstore.swagger.io/v2/store/order/{orderId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("DELETE");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`DELETE /store/order/{orderId}`

*Delete purchase order by ID*

For valid response try integer IDs with value < 1000. Anything above 1000 or nonintegers will generate API errors

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
orderId|path|string|true|ID of the order that needs to be deleted


### Responses

Status|Meaning|Description|Schema
---|---|---|---|
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid ID supplied|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Order not found|None

<aside class="success">
This operation does not require authentication
</aside>

# user

Operations about user

## createUser

> Code samples

```shell
# You can also use wget
curl -X POST http://petstore.swagger.io/v2/user \
  -H 'Content-Type: application/json'

```

```http
POST http://petstore.swagger.io/v2/user HTTP/1.1
Host: petstore.swagger.io
Content-Type: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json'

};

$.ajax({
  url: 'http://petstore.swagger.io/v2/user',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "id": 0,
  "username": "John78",
  "firstName": "John",
  "lastName": "Smith",
  "email": "john.smith@example.com",
  "password": "drowssaP123",
  "phone": "+1-202-555-0192",
  "userStatus": 0
}';
const headers = {
  'Content-Type':'application/json'

};

fetch('http://petstore.swagger.io/v2/user',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json'
}

result = RestClient.post 'http://petstore.swagger.io/v2/user',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Content-Type': 'application/json'
}

r = requests.post('http://petstore.swagger.io/v2/user', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("http://petstore.swagger.io/v2/user");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`POST /user`

*Create user*

This can only be done by the logged in user.

> Body parameter

```json
{
  "id": 0,
  "username": "John78",
  "firstName": "John",
  "lastName": "Smith",
  "email": "john.smith@example.com",
  "password": "drowssaP123",
  "phone": "+1-202-555-0192",
  "userStatus": 0
}
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
body|body|[User](#schemauser)|true|Created user object
» id|body|integer(int64)|false|No description
» username|body|string|false|User supplied username
» firstName|body|string|false|User first name
» lastName|body|string|false|User last name
» email|body|string(email)|false|User email address
» password|body|string(password)|false|User password, MUST contain a mix of upper and lower case letters, as well as digits
» phone|body|string|false|User phone number in international format
» userStatus|body|integer(int32)|false|User status


### Responses

Status|Meaning|Description|Schema
---|---|---|---|
default|Default|successful operation|None

<aside class="success">
This operation does not require authentication
</aside>

## getUserByName

> Code samples

```shell
# You can also use wget
curl -X GET http://petstore.swagger.io/v2/user/{username} \
  -H 'Accept: application/xml'

```

```http
GET http://petstore.swagger.io/v2/user/{username} HTTP/1.1
Host: petstore.swagger.io

Accept: application/xml

```

```javascript
var headers = {
  'Accept':'application/xml'

};

$.ajax({
  url: 'http://petstore.swagger.io/v2/user/{username}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/xml'

};

fetch('http://petstore.swagger.io/v2/user/{username}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/xml'
}

result = RestClient.get 'http://petstore.swagger.io/v2/user/{username}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/xml'
}

r = requests.get('http://petstore.swagger.io/v2/user/{username}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("http://petstore.swagger.io/v2/user/{username}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /user/{username}`

*Get user by user name*

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
username|path|string|true|The name that needs to be fetched. Use user1 for testing. 


> Example responses

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<User>
  <id>0</id>
  <username>John78</username>
  <firstName>John</firstName>
  <lastName>Smith</lastName>
  <email>john.smith@example.com</email>
  <password>drowssaP123</password>
  <phone>+1-202-555-0192</phone>
  <userStatus>0</userStatus>
</User>
```
```json
{
  "id": 0,
  "username": "John78",
  "firstName": "John",
  "lastName": "Smith",
  "email": "john.smith@example.com",
  "password": "drowssaP123",
  "phone": "+1-202-555-0192",
  "userStatus": 0
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[User](#schemauser)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid username supplied|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|User not found|None

<aside class="success">
This operation does not require authentication
</aside>

## updateUser

> Code samples

```shell
# You can also use wget
curl -X PUT http://petstore.swagger.io/v2/user/{username} \
  -H 'Content-Type: application/json'

```

```http
PUT http://petstore.swagger.io/v2/user/{username} HTTP/1.1
Host: petstore.swagger.io
Content-Type: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json'

};

$.ajax({
  url: 'http://petstore.swagger.io/v2/user/{username}',
  method: 'put',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "id": 0,
  "username": "John78",
  "firstName": "John",
  "lastName": "Smith",
  "email": "john.smith@example.com",
  "password": "drowssaP123",
  "phone": "+1-202-555-0192",
  "userStatus": 0
}';
const headers = {
  'Content-Type':'application/json'

};

fetch('http://petstore.swagger.io/v2/user/{username}',
{
  method: 'PUT',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json'
}

result = RestClient.put 'http://petstore.swagger.io/v2/user/{username}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Content-Type': 'application/json'
}

r = requests.put('http://petstore.swagger.io/v2/user/{username}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("http://petstore.swagger.io/v2/user/{username}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PUT");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`PUT /user/{username}`

*Updated user*

This can only be done by the logged in user.

> Body parameter

```json
{
  "id": 0,
  "username": "John78",
  "firstName": "John",
  "lastName": "Smith",
  "email": "john.smith@example.com",
  "password": "drowssaP123",
  "phone": "+1-202-555-0192",
  "userStatus": 0
}
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
username|path|string|true|name that need to be deleted
body|body|[User](#schemauser)|true|Updated user object
» id|body|integer(int64)|false|No description
» username|body|string|false|User supplied username
» firstName|body|string|false|User first name
» lastName|body|string|false|User last name
» email|body|string(email)|false|User email address
» password|body|string(password)|false|User password, MUST contain a mix of upper and lower case letters, as well as digits
» phone|body|string|false|User phone number in international format
» userStatus|body|integer(int32)|false|User status


### Responses

Status|Meaning|Description|Schema
---|---|---|---|
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid user supplied|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|User not found|None

<aside class="success">
This operation does not require authentication
</aside>

## deleteUser

> Code samples

```shell
# You can also use wget
curl -X DELETE http://petstore.swagger.io/v2/user/{username}

```

```http
DELETE http://petstore.swagger.io/v2/user/{username} HTTP/1.1
Host: petstore.swagger.io


```

```javascript

$.ajax({
  url: 'http://petstore.swagger.io/v2/user/{username}',
  method: 'delete',

  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

fetch('http://petstore.swagger.io/v2/user/{username}',
{
  method: 'DELETE'

})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'


result = RestClient.delete 'http://petstore.swagger.io/v2/user/{username}',
  params: {
  }

p JSON.parse(result)
```

```python
import requests

r = requests.delete('http://petstore.swagger.io/v2/user/{username}', params={

)

print r.json()
```

```java
URL obj = new URL("http://petstore.swagger.io/v2/user/{username}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("DELETE");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`DELETE /user/{username}`

*Delete user*

This can only be done by the logged in user.

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
username|path|string|true|The name that needs to be deleted


### Responses

Status|Meaning|Description|Schema
---|---|---|---|
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid username supplied|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|User not found|None

<aside class="success">
This operation does not require authentication
</aside>

## createUsersWithArrayInput

> Code samples

```shell
# You can also use wget
curl -X POST http://petstore.swagger.io/v2/user/createWithArray \
  -H 'Content-Type: application/json'

```

```http
POST http://petstore.swagger.io/v2/user/createWithArray HTTP/1.1
Host: petstore.swagger.io
Content-Type: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json'

};

$.ajax({
  url: 'http://petstore.swagger.io/v2/user/createWithArray',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '[
  {}
]';
const headers = {
  'Content-Type':'application/json'

};

fetch('http://petstore.swagger.io/v2/user/createWithArray',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json'
}

result = RestClient.post 'http://petstore.swagger.io/v2/user/createWithArray',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Content-Type': 'application/json'
}

r = requests.post('http://petstore.swagger.io/v2/user/createWithArray', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("http://petstore.swagger.io/v2/user/createWithArray");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`POST /user/createWithArray`

*Creates list of users with given input array*

> Body parameter

```json
[
  {
    "id": 0,
    "username": "John78",
    "firstName": "John",
    "lastName": "Smith",
    "email": "john.smith@example.com",
    "password": "drowssaP123",
    "phone": "+1-202-555-0192",
    "userStatus": 0
  }
]
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
body|body|[UserArray](#schema+userarray)|true|List of user object


### Responses

Status|Meaning|Description|Schema
---|---|---|---|
default|Default|successful operation|None

<aside class="success">
This operation does not require authentication
</aside>

## createUsersWithListInput

> Code samples

```shell
# You can also use wget
curl -X POST http://petstore.swagger.io/v2/user/createWithList \
  -H 'Content-Type: application/json'

```

```http
POST http://petstore.swagger.io/v2/user/createWithList HTTP/1.1
Host: petstore.swagger.io
Content-Type: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json'

};

$.ajax({
  url: 'http://petstore.swagger.io/v2/user/createWithList',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '[
  {
    "id": 0,
    "username": "John78",
    "firstName": "John",
    "lastName": "Smith",
    "email": "john.smith@example.com",
    "password": "drowssaP123",
    "phone": "+1-202-555-0192",
    "userStatus": 0
  }
]';
const headers = {
  'Content-Type':'application/json'

};

fetch('http://petstore.swagger.io/v2/user/createWithList',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json'
}

result = RestClient.post 'http://petstore.swagger.io/v2/user/createWithList',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Content-Type': 'application/json'
}

r = requests.post('http://petstore.swagger.io/v2/user/createWithList', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("http://petstore.swagger.io/v2/user/createWithList");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`POST /user/createWithList`

*Creates list of users with given input array*

> Body parameter

```json
[
  {
    "id": 0,
    "username": "John78",
    "firstName": "John",
    "lastName": "Smith",
    "email": "john.smith@example.com",
    "password": "drowssaP123",
    "phone": "+1-202-555-0192",
    "userStatus": 0
  }
]
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
body|body|[UserArray](#schema+userarray)|true|List of user object


### Responses

Status|Meaning|Description|Schema
---|---|---|---|
default|Default|successful operation|None

<aside class="success">
This operation does not require authentication
</aside>

## loginUser

> Code samples

```shell
# You can also use wget
curl -X GET http://petstore.swagger.io/v2/user/login?username=string&password=string \
  -H 'Accept: application/xml'

```

```http
GET http://petstore.swagger.io/v2/user/login?username=string&password=string HTTP/1.1
Host: petstore.swagger.io

Accept: application/xml

```

```javascript
var headers = {
  'Accept':'application/xml'

};

$.ajax({
  url: 'http://petstore.swagger.io/v2/user/login',
  method: 'get',
  data: '?username=string&password=string',
  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/xml'

};

fetch('http://petstore.swagger.io/v2/user/login?username=string&password=string',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/xml'
}

result = RestClient.get 'http://petstore.swagger.io/v2/user/login',
  params: {
  'username' => 'string',
'password' => 'string'
}, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/xml'
}

r = requests.get('http://petstore.swagger.io/v2/user/login', params={
  'username': 'string',  'password': 'string'
}, headers = headers)

print r.json()
```

```java
URL obj = new URL("http://petstore.swagger.io/v2/user/login?username=string&password=string");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /user/login`

*Logs user into the system*

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
username|query|string|true|The user name for login
password|query|string|true|The password for login in clear text


> Example responses

```json
"string"
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|string
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid username/password supplied|None

### Response Headers

Status|Header|Type|Format|Description
---|---|---|---|---|
200|X-Rate-Limit|integer|int32|calls per hour allowed by the user
200|X-Expires-After|string|date-time|date in UTC when toekn expires

<aside class="success">
This operation does not require authentication
</aside>

## logoutUser

> Code samples

```shell
# You can also use wget
curl -X GET http://petstore.swagger.io/v2/user/logout

```

```http
GET http://petstore.swagger.io/v2/user/logout HTTP/1.1
Host: petstore.swagger.io


```

```javascript

$.ajax({
  url: 'http://petstore.swagger.io/v2/user/logout',
  method: 'get',

  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

fetch('http://petstore.swagger.io/v2/user/logout',
{
  method: 'GET'

})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'


result = RestClient.get 'http://petstore.swagger.io/v2/user/logout',
  params: {
  }

p JSON.parse(result)
```

```python
import requests

r = requests.get('http://petstore.swagger.io/v2/user/logout', params={

)

print r.json()
```

```java
URL obj = new URL("http://petstore.swagger.io/v2/user/logout");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /user/logout`

*Logs out current logged in user session*

### Responses

Status|Meaning|Description|Schema
---|---|---|---|
default|Default|successful operation|None

<aside class="success">
This operation does not require authentication
</aside>

# Schemas

## ApiResponse

<a name="schemaapiresponse"></a>

```json
{
  "code": 0,
  "type": "string",
  "message": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
code|integer(int32)|false|No description
type|string|false|No description
message|string|false|No description



## Cat

<a name="schemacat"></a>

```json
{
  "petType": "string",
  "id": 0,
  "category": {
    "id": 0,
    "name": "string"
  },
  "name": "Guru",
  "photoUrls": [
    "string"
  ],
  "tags": [
    {
      "id": 0,
      "name": "string"
    }
  ],
  "status": "available",
  "huntingSkill": "lazy"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
petType|string|false|Type of a pet
id|integer(int64)|false|Pet ID
category|[Category](#schemacategory)|false|Categories this pet belongs to
» id|integer(int64)|false|Category ID
» name|string|false|Category name
name|string|true|The name given to a pet
status|string|false|Pet status in the store
huntingSkill|string|false|The measured skill for hunting
photoUrls|[string(url)]|false|The list of URL to a cute photos featuring pet
tags|[[Tag](#schematag)]|false|Tags attached to the pet
» id|integer(int64)|false|Tag ID
» name|string|false|Tag name


#### Enumerated Values

|Property|Value|
|---|---|
status|available|
status|pending|
status|sold|
huntingSkill|clueless|
huntingSkill|lazy|
huntingSkill|adventurous|
huntingSkill|aggressive|


## Category

<a name="schemacategory"></a>

```json
{
  "id": 0,
  "name": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
id|integer(int64)|false|Category ID
name|string|false|Category name



## Dog

<a name="schemadog"></a>

```json
{
  "petType": "string",
  "id": 0,
  "category": {
    "id": 0,
    "name": "string"
  },
  "name": "Guru",
  "photoUrls": [
    "string"
  ],
  "tags": [
    {
      "id": 0,
      "name": "string"
    }
  ],
  "status": "available",
  "packSize": 1
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
petType|string|false|Type of a pet
id|integer(int64)|false|Pet ID
category|[Category](#schemacategory)|false|Categories this pet belongs to
» id|integer(int64)|false|Category ID
» name|string|false|Category name
name|string|true|The name given to a pet
status|string|false|Pet status in the store
packSize|integer(int32)|false|The size of the pack the dog is from
photoUrls|[string(url)]|false|The list of URL to a cute photos featuring pet
tags|[[Tag](#schematag)]|false|Tags attached to the pet
» id|integer(int64)|false|Tag ID
» name|string|false|Tag name


#### Enumerated Values

|Property|Value|
|---|---|
status|available|
status|pending|
status|sold|


## HoneyBee

<a name="schemahoneybee"></a>

```json
{
  "petType": "string",
  "id": 0,
  "category": {
    "id": 0,
    "name": "string"
  },
  "name": "Guru",
  "photoUrls": [
    "string"
  ],
  "tags": [
    {
      "id": 0,
      "name": "string"
    }
  ],
  "status": "available",
  "honeyPerDay": 3.14
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
petType|string|false|Type of a pet
id|integer(int64)|false|Pet ID
category|[Category](#schemacategory)|false|Categories this pet belongs to
» id|integer(int64)|false|Category ID
» name|string|false|Category name
name|string|true|The name given to a pet
status|string|false|Pet status in the store
honeyPerDay|number|false|Average amount of honey produced per day in ounces
photoUrls|[string(url)]|false|The list of URL to a cute photos featuring pet
tags|[[Tag](#schematag)]|false|Tags attached to the pet
» id|integer(int64)|false|Tag ID
» name|string|false|Tag name


#### Enumerated Values

|Property|Value|
|---|---|
status|available|
status|pending|
status|sold|


## Id

<a name="schemaid"></a>

```json
0 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
simple|integer(int64)|false|No description



## Order

<a name="schemaorder"></a>

```json
{
  "id": 0,
  "petId": 0,
  "quantity": 1,
  "shipDate": "2017-10-09T08:59:09Z",
  "status": "placed",
  "complete": false
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
id|integer(int64)|false|Order ID
petId|integer(int64)|false|Pet ID
quantity|integer(int32)|false|No description
shipDate|string(date-time)|false|Estimated ship date
status|string|false|Order Status
complete|boolean|false|Indicates whenever order was completed or not


#### Enumerated Values

|Property|Value|
|---|---|
status|placed|
status|approved|
status|delivered|


## Pet

<a name="schemapet"></a>

```json
{
  "petType": "string",
  "id": 0,
  "category": {
    "id": 0,
    "name": "string"
  },
  "name": "Guru",
  "photoUrls": [
    "string"
  ],
  "tags": [
    {
      "id": 0,
      "name": "string"
    }
  ],
  "status": "available"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
petType|string|false|Type of a pet
id|integer(int64)|false|Pet ID
category|[Category](#schemacategory)|false|Categories this pet belongs to
» id|integer(int64)|false|Category ID
» name|string|false|Category name
name|string|true|The name given to a pet
status|string|false|Pet status in the store
photoUrls|[string(url)]|false|The list of URL to a cute photos featuring pet
tags|[[Tag](#schematag)]|false|Tags attached to the pet
» id|integer(int64)|false|Tag ID
» name|string|false|Tag name


#### Enumerated Values

|Property|Value|
|---|---|
status|available|
status|pending|
status|sold|


## Tag

<a name="schematag"></a>

```json
{
  "id": 0,
  "name": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
id|integer(int64)|false|Tag ID
name|string|false|Tag name



## User

<a name="schemauser"></a>

```json
{
  "id": 0,
  "username": "John78",
  "firstName": "John",
  "lastName": "Smith",
  "email": "john.smith@example.com",
  "password": "drowssaP123",
  "phone": "+1-202-555-0192",
  "userStatus": 0
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
id|integer(int64)|false|No description
username|string|false|User supplied username
firstName|string|false|User first name
lastName|string|false|User last name
email|string(email)|false|User email address
password|string(password)|false|User password, MUST contain a mix of upper and lower case letters, as well as digits
phone|string|false|User phone number in international format
userStatus|integer(int32)|false|User status





