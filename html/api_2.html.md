---
title: Scotibank BaaS - Security Service v0.0.1
language_tabs:
  - shell: Shell
  - http: HTTP
  - javascript: JavaScript
  - javascript--nodejs: Node.JS
  - ruby: Ruby
  - python: Python
  - java: Java
toc_footers: []
includes: []
search: true
highlight_theme: darkula
---

# Scotibank BaaS - Security Service v0.0.1

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

This domain include services to apply security to BaaS operations.

Base URLs:

* <a href="/v0/">/v0/</a>





# Signatures

Signatures to be applied to an operation

## save_signature

> Code samples

```shell
# You can also use wget
curl -X POST /v0//secutiry/signatures/ \
  -H 'Authorization: string' \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST /v0//secutiry/signatures/ HTTP/1.1
Host: null
Content-Type: application/json
Accept: application/json
Authorization: string

```

```javascript
var headers = {
  'Authorization':'string',
  'Content-Type':'application/json',
  'Accept':'application/json'

};

$.ajax({
  url: '/v0//secutiry/signatures/',
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
  "operation_url": "/accounts/wire-transfer/123455",
  "operation_channel": "MOBILE"
}';
const headers = {
  'Authorization':'string',
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('/v0//secutiry/signatures/',
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
  'Authorization' => 'string',
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.post '/v0//secutiry/signatures/',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Authorization': 'string',
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.post('/v0//secutiry/signatures/', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("/v0//secutiry/signatures/");
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

`POST /secutiry/signatures/`

*creates a new signature for an operation*

Save a new signature

> Body parameter

```json
{
  "operation_url": "/accounts/wire-transfer/123455",
  "operation_channel": "MOBILE"
}
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
Authorization|header|string|true|the auth token
body|body|object|true|Body of signature
» operation_url|body|string|false|URL for the operation in progress
» operation_channel|body|string|false|Channel that initiates the operation


> Example responses

```json
{
  "signature_key": "123455",
  "operation_url": "/accounts/wire-transfer/123455",
  "operation_channel": "MOBILE",
  "status": "NEW",
  "expiration_date": "2017-12-31T23:59:59",
  "signers": [
    {
      "sign_method": 1,
      "sign_status": "PENDING, OK, NOK, LOCKED",
      "sign_completeness_porcentage": 50,
      "signatures": [
        {
          "signature": "{ sign_method: OTP, value: 'GH5T', ... }",
          "status": "OK",
          "signature_date": "2017-12-31T23:59:59"
        }
      ],
      "user_url": "/users/1234567",
      "signant_type": "REQUIRED"
    }
  ]
}
```
```json
{
  "id": "85ca3108-8e11-4ad2-b174-1fc3e5dbef1b",
  "code": "001-001-0001",
  "message": "User or Password Invalid",
  "path": "/CL/v1/customerWebSiteLogin",
  "timestamp": 1482253855188,
  "requestId": "11235f"
}
```
```json
{
  "id": "85ca3108-8e11-4ad2-b174-1fc3e5dbef1b",
  "code": "001-001-0001",
  "message": "User or Password Invalid",
  "path": "/CL/v1/customerWebSiteLogin",
  "timestamp": 1482253855188,
  "requestId": "11235f"
}
```
```json
{
  "id": "85ca3108-8e11-4ad2-b174-1fc3e5dbef1b",
  "code": "001-001-0001",
  "message": "User or Password Invalid",
  "path": "/CL/v1/customerWebSiteLogin",
  "timestamp": 1482253855188,
  "requestId": "11235f"
}
```
```json
{
  "id": "85ca3108-8e11-4ad2-b174-1fc3e5dbef1b",
  "code": "001-001-0001",
  "message": "User or Password Invalid",
  "path": "/CL/v1/customerWebSiteLogin",
  "timestamp": 1482253855188,
  "requestId": "11235f"
}
```
```json
{
  "id": "85ca3108-8e11-4ad2-b174-1fc3e5dbef1b",
  "code": "001-001-0001",
  "message": "User or Password Invalid",
  "path": "/CL/v1/customerWebSiteLogin",
  "timestamp": 1482253855188,
  "requestId": "11235f"
}
```
```json
{
  "id": "85ca3108-8e11-4ad2-b174-1fc3e5dbef1b",
  "code": "001-001-0001",
  "message": "User or Password Invalid",
  "path": "/CL/v1/customerWebSiteLogin",
  "timestamp": 1482253855188,
  "requestId": "11235f"
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|return the new signature|[OperationSignature](#schemaoperationsignature)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Indicates that the server could not understand the request. This is not the same as 422 which indicates a validation error|[Error](#schemaerror)
401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized.  This will be returned when no authentication information is provided.|[Error](#schemaerror)
403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|The principal associated with the request does not have sufficient rights to preform this operation on the requested resource.|[Error](#schemaerror)
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The requested resource was not found.|[Error](#schemaerror)
422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|The request was syntactically correct but was not semantically correct. Useally indicating a validation problem.|[Error](#schemaerror)
500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|[Error](#schemaerror)

<aside class="success">
This operation does not require authentication
</aside>

## get_signatures

> Code samples

```shell
# You can also use wget
curl -X GET /v0//secutiry/signatures/ \
  -H 'Authorization: string' \
  -H 'Accept: application/json'

```

```http
GET /v0//secutiry/signatures/ HTTP/1.1
Host: null

Accept: application/json
Authorization: string

```

```javascript
var headers = {
  'Authorization':'string',
  'Accept':'application/json'

};

$.ajax({
  url: '/v0//secutiry/signatures/',
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
  'Authorization':'string',
  'Accept':'application/json'

};

fetch('/v0//secutiry/signatures/',
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
  'Authorization' => 'string',
  'Accept' => 'application/json'
}

result = RestClient.get '/v0//secutiry/signatures/',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Authorization': 'string',
  'Accept': 'application/json'
}

r = requests.get('/v0//secutiry/signatures/', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("/v0//secutiry/signatures/");
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

`GET /secutiry/signatures/`

*Get signatures*

Get signatures

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
Authorization|header|string|true|the auth token
status|query|string|false|filter by status


> Example responses

```json
[
  {
    "signature_key": "123455",
    "operation_url": "/accounts/wire-transfer/123455",
    "operation_channel": "MOBILE",
    "status": "NEW",
    "expiration_date": "2017-12-31T23:59:59",
    "signers": [
      {
        "sign_method": 1,
        "sign_status": "PENDING, OK, NOK, LOCKED",
        "sign_completeness_porcentage": 50,
        "signatures": [
          {
            "signature": "{ sign_method: OTP, value: 'GH5T', ... }",
            "status": "OK",
            "signature_date": "2017-12-31T23:59:59"
          }
        ],
        "user_url": "/users/1234567",
        "signant_type": "REQUIRED"
      }
    ]
  }
]
```
```json
{
  "id": "85ca3108-8e11-4ad2-b174-1fc3e5dbef1b",
  "code": "001-001-0001",
  "message": "User or Password Invalid",
  "path": "/CL/v1/customerWebSiteLogin",
  "timestamp": 1482253855188,
  "requestId": "11235f"
}
```
```json
{
  "id": "85ca3108-8e11-4ad2-b174-1fc3e5dbef1b",
  "code": "001-001-0001",
  "message": "User or Password Invalid",
  "path": "/CL/v1/customerWebSiteLogin",
  "timestamp": 1482253855188,
  "requestId": "11235f"
}
```
```json
{
  "id": "85ca3108-8e11-4ad2-b174-1fc3e5dbef1b",
  "code": "001-001-0001",
  "message": "User or Password Invalid",
  "path": "/CL/v1/customerWebSiteLogin",
  "timestamp": 1482253855188,
  "requestId": "11235f"
}
```
```json
{
  "id": "85ca3108-8e11-4ad2-b174-1fc3e5dbef1b",
  "code": "001-001-0001",
  "message": "User or Password Invalid",
  "path": "/CL/v1/customerWebSiteLogin",
  "timestamp": 1482253855188,
  "requestId": "11235f"
}
```
```json
{
  "id": "85ca3108-8e11-4ad2-b174-1fc3e5dbef1b",
  "code": "001-001-0001",
  "message": "User or Password Invalid",
  "path": "/CL/v1/customerWebSiteLogin",
  "timestamp": 1482253855188,
  "requestId": "11235f"
}
```
```json
{
  "id": "85ca3108-8e11-4ad2-b174-1fc3e5dbef1b",
  "code": "001-001-0001",
  "message": "User or Password Invalid",
  "path": "/CL/v1/customerWebSiteLogin",
  "timestamp": 1482253855188,
  "requestId": "11235f"
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|return array of signatures|Inline
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Indicates that the server could not understand the request. This is not the same as 422 which indicates a validation error|[Error](#schemaerror)
401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized.  This will be returned when no authentication information is provided.|[Error](#schemaerror)
403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|The principal associated with the request does not have sufficient rights to preform this operation on the requested resource.|[Error](#schemaerror)
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The requested resource was not found.|[Error](#schemaerror)
422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|The request was syntactically correct but was not semantically correct. Useally indicating a validation problem.|[Error](#schemaerror)
500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|[Error](#schemaerror)

### Response Schema

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
anonymous|[[OperationSignature](#schemaoperationsignature)]|false|No description
» signature_key|string|false|unique key generated by BaaS for this operation signature
» operation_url|string|false|URL for the operation in progress
» operation_channel|string|false|Channel that initiates the operation
» status|string|false|status of the authorization flow
» expiration_date|string(date)|false|Expiration date for the signature in ISO 8601 full-format
» signers|[[Signer](#schemasigner)]|false|No description
»» sign_method|string|true|available sign methods for the current user, like OTP, password, fingerprint, ect
»» sign_status|string|true|Status of validation in operation
»» sign_completeness_porcentage|integer|true|percentage of sign to complete the authorization of operation
»» user_url|string|false|Status of validation in operation
»» signant_type|string|false|Defines the required or optional level for this sign
»» signatures|[[Signature](#schemasignature)]|false|No description
»»» signature|string|false|available sign methods for the current user, like OTP, password, fingerprint, ect
»»» status|string|false|One of the following status OK, KO, PENDING, RETRY
»»» signature_date|string(date)|false|Signature date



<aside class="success">
This operation does not require authentication
</aside>

## put_signature

> Code samples

```shell
# You can also use wget
curl -X POST /v0//security/signatures/{signature-key}/signers/{sign-index}/signatures \
  -H 'Authorization: string' \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST /v0//security/signatures/{signature-key}/signers/{sign-index}/signatures HTTP/1.1
Host: null
Content-Type: application/json
Accept: application/json
Authorization: string

```

```javascript
var headers = {
  'Authorization':'string',
  'Content-Type':'application/json',
  'Accept':'application/json'

};

$.ajax({
  url: '/v0//security/signatures/{signature-key}/signers/{sign-index}/signatures',
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
  "signature": "{ sign_method: OTP, value: 'GH5T', ... }"
}';
const headers = {
  'Authorization':'string',
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('/v0//security/signatures/{signature-key}/signers/{sign-index}/signatures',
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
  'Authorization' => 'string',
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.post '/v0//security/signatures/{signature-key}/signers/{sign-index}/signatures',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Authorization': 'string',
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.post('/v0//security/signatures/{signature-key}/signers/{sign-index}/signatures', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("/v0//security/signatures/{signature-key}/signers/{sign-index}/signatures");
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

`POST /security/signatures/{signature-key}/signers/{sign-index}/signatures`

*Update an ongoing signing operation*

Update an ongoing signing

> Body parameter

```json
{
  "signature": "{ sign_method: OTP, value: 'GH5T', ... }"
}
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
Authorization|header|string|true|the auth token
signature-key|path|string|true|id for the current operation
sign-index|path|string|true|Index in the signs array
body|body|object|true|Body of signature
» signature|body|string|false|available sign methods for the current user, like OTP, password, fingerprint, ect


> Example responses

```json
{
  "signature": "{ sign_method: OTP, value: 'GH5T', ... }",
  "status": "OK",
  "signature_date": "2017-12-31T23:59:59"
}
```
```json
{
  "id": "85ca3108-8e11-4ad2-b174-1fc3e5dbef1b",
  "code": "001-001-0001",
  "message": "User or Password Invalid",
  "path": "/CL/v1/customerWebSiteLogin",
  "timestamp": 1482253855188,
  "requestId": "11235f"
}
```
```json
{
  "id": "85ca3108-8e11-4ad2-b174-1fc3e5dbef1b",
  "code": "001-001-0001",
  "message": "User or Password Invalid",
  "path": "/CL/v1/customerWebSiteLogin",
  "timestamp": 1482253855188,
  "requestId": "11235f"
}
```
```json
{
  "id": "85ca3108-8e11-4ad2-b174-1fc3e5dbef1b",
  "code": "001-001-0001",
  "message": "User or Password Invalid",
  "path": "/CL/v1/customerWebSiteLogin",
  "timestamp": 1482253855188,
  "requestId": "11235f"
}
```
```json
{
  "id": "85ca3108-8e11-4ad2-b174-1fc3e5dbef1b",
  "code": "001-001-0001",
  "message": "User or Password Invalid",
  "path": "/CL/v1/customerWebSiteLogin",
  "timestamp": 1482253855188,
  "requestId": "11235f"
}
```
```json
{
  "id": "85ca3108-8e11-4ad2-b174-1fc3e5dbef1b",
  "code": "001-001-0001",
  "message": "User or Password Invalid",
  "path": "/CL/v1/customerWebSiteLogin",
  "timestamp": 1482253855188,
  "requestId": "11235f"
}
```
```json
{
  "id": "85ca3108-8e11-4ad2-b174-1fc3e5dbef1b",
  "code": "001-001-0001",
  "message": "User or Password Invalid",
  "path": "/CL/v1/customerWebSiteLogin",
  "timestamp": 1482253855188,
  "requestId": "11235f"
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|return the status of the signature after update|[Signature](#schemasignature)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Indicates that the server could not understand the request. This is not the same as 422 which indicates a validation error|[Error](#schemaerror)
401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized.  This will be returned when no authentication information is provided.|[Error](#schemaerror)
403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|The principal associated with the request does not have sufficient rights to preform this operation on the requested resource.|[Error](#schemaerror)
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The requested resource was not found.|[Error](#schemaerror)
422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|The request was syntactically correct but was not semantically correct. Useally indicating a validation problem.|[Error](#schemaerror)
500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|[Error](#schemaerror)

<aside class="success">
This operation does not require authentication
</aside>

# Devices

## save_sign

> Code samples

```shell
# You can also use wget
curl -X POST /v0//secutiry/signature-devices \
  -H 'Authorization: string' \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST /v0//secutiry/signature-devices HTTP/1.1
Host: null
Content-Type: application/json
Accept: application/json
Authorization: string

```

```javascript
var headers = {
  'Authorization':'string',
  'Content-Type':'application/json',
  'Accept':'application/json'

};

$.ajax({
  url: '/v0//secutiry/signature-devices',
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
  "signature_device_id": 1234343,
  "device_type": "TOKEN"
}';
const headers = {
  'Authorization':'string',
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('/v0//secutiry/signature-devices',
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
  'Authorization' => 'string',
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.post '/v0//secutiry/signature-devices',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Authorization': 'string',
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.post('/v0//secutiry/signature-devices', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("/v0//secutiry/signature-devices");
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

`POST /secutiry/signature-devices`

*Save a new sign method*

Save a new sign method

> Body parameter

```json
{
  "signature_device_id": 1234343,
  "device_type": "TOKEN"
}
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
Authorization|header|string|true|the auth token
body|body|[SignatureDevice](#schemasignaturedevice)|true|Body of new sign
» signature_device_id|body|string|false|unique code usually provided by the device vendor
» device_type|body|string|false|device type code


> Example responses

```json
{
  "signature_device_id": 1234343,
  "device_type": "TOKEN"
}
```
```json
{
  "id": "85ca3108-8e11-4ad2-b174-1fc3e5dbef1b",
  "code": "001-001-0001",
  "message": "User or Password Invalid",
  "path": "/CL/v1/customerWebSiteLogin",
  "timestamp": 1482253855188,
  "requestId": "11235f"
}
```
```json
{
  "id": "85ca3108-8e11-4ad2-b174-1fc3e5dbef1b",
  "code": "001-001-0001",
  "message": "User or Password Invalid",
  "path": "/CL/v1/customerWebSiteLogin",
  "timestamp": 1482253855188,
  "requestId": "11235f"
}
```
```json
{
  "id": "85ca3108-8e11-4ad2-b174-1fc3e5dbef1b",
  "code": "001-001-0001",
  "message": "User or Password Invalid",
  "path": "/CL/v1/customerWebSiteLogin",
  "timestamp": 1482253855188,
  "requestId": "11235f"
}
```
```json
{
  "id": "85ca3108-8e11-4ad2-b174-1fc3e5dbef1b",
  "code": "001-001-0001",
  "message": "User or Password Invalid",
  "path": "/CL/v1/customerWebSiteLogin",
  "timestamp": 1482253855188,
  "requestId": "11235f"
}
```
```json
{
  "id": "85ca3108-8e11-4ad2-b174-1fc3e5dbef1b",
  "code": "001-001-0001",
  "message": "User or Password Invalid",
  "path": "/CL/v1/customerWebSiteLogin",
  "timestamp": 1482253855188,
  "requestId": "11235f"
}
```
```json
{
  "id": "85ca3108-8e11-4ad2-b174-1fc3e5dbef1b",
  "code": "001-001-0001",
  "message": "User or Password Invalid",
  "path": "/CL/v1/customerWebSiteLogin",
  "timestamp": 1482253855188,
  "requestId": "11235f"
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|returns the new signature device|[SignatureDevice](#schemasignaturedevice)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Indicates that the server could not understand the request. This is not the same as 422 which indicates a validation error|[Error](#schemaerror)
401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized.  This will be returned when no authentication information is provided.|[Error](#schemaerror)
403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|The principal associated with the request does not have sufficient rights to preform this operation on the requested resource.|[Error](#schemaerror)
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The requested resource was not found.|[Error](#schemaerror)
422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|The request was syntactically correct but was not semantically correct. Useally indicating a validation problem.|[Error](#schemaerror)
500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|[Error](#schemaerror)

<aside class="success">
This operation does not require authentication
</aside>

## get_signs

> Code samples

```shell
# You can also use wget
curl -X GET /v0//secutiry/signature-devices \
  -H 'Authorization: string' \
  -H 'Accept: application/json'

```

```http
GET /v0//secutiry/signature-devices HTTP/1.1
Host: null

Accept: application/json
Authorization: string

```

```javascript
var headers = {
  'Authorization':'string',
  'Accept':'application/json'

};

$.ajax({
  url: '/v0//secutiry/signature-devices',
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
  'Authorization':'string',
  'Accept':'application/json'

};

fetch('/v0//secutiry/signature-devices',
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
  'Authorization' => 'string',
  'Accept' => 'application/json'
}

result = RestClient.get '/v0//secutiry/signature-devices',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Authorization': 'string',
  'Accept': 'application/json'
}

r = requests.get('/v0//secutiry/signature-devices', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("/v0//secutiry/signature-devices");
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

`GET /secutiry/signature-devices`

*Get sign methods availables*

Get sign method

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
Authorization|header|string|true|the auth token


> Example responses

```json
[
  {
    "signature_device_id": 1234343,
    "device_type": "TOKEN"
  }
]
```
```json
{
  "id": "85ca3108-8e11-4ad2-b174-1fc3e5dbef1b",
  "code": "001-001-0001",
  "message": "User or Password Invalid",
  "path": "/CL/v1/customerWebSiteLogin",
  "timestamp": 1482253855188,
  "requestId": "11235f"
}
```
```json
{
  "id": "85ca3108-8e11-4ad2-b174-1fc3e5dbef1b",
  "code": "001-001-0001",
  "message": "User or Password Invalid",
  "path": "/CL/v1/customerWebSiteLogin",
  "timestamp": 1482253855188,
  "requestId": "11235f"
}
```
```json
{
  "id": "85ca3108-8e11-4ad2-b174-1fc3e5dbef1b",
  "code": "001-001-0001",
  "message": "User or Password Invalid",
  "path": "/CL/v1/customerWebSiteLogin",
  "timestamp": 1482253855188,
  "requestId": "11235f"
}
```
```json
{
  "id": "85ca3108-8e11-4ad2-b174-1fc3e5dbef1b",
  "code": "001-001-0001",
  "message": "User or Password Invalid",
  "path": "/CL/v1/customerWebSiteLogin",
  "timestamp": 1482253855188,
  "requestId": "11235f"
}
```
```json
{
  "id": "85ca3108-8e11-4ad2-b174-1fc3e5dbef1b",
  "code": "001-001-0001",
  "message": "User or Password Invalid",
  "path": "/CL/v1/customerWebSiteLogin",
  "timestamp": 1482253855188,
  "requestId": "11235f"
}
```
```json
{
  "id": "85ca3108-8e11-4ad2-b174-1fc3e5dbef1b",
  "code": "001-001-0001",
  "message": "User or Password Invalid",
  "path": "/CL/v1/customerWebSiteLogin",
  "timestamp": 1482253855188,
  "requestId": "11235f"
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|return array of signatures|Inline
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Indicates that the server could not understand the request. This is not the same as 422 which indicates a validation error|[Error](#schemaerror)
401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized.  This will be returned when no authentication information is provided.|[Error](#schemaerror)
403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|The principal associated with the request does not have sufficient rights to preform this operation on the requested resource.|[Error](#schemaerror)
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The requested resource was not found.|[Error](#schemaerror)
422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|The request was syntactically correct but was not semantically correct. Useally indicating a validation problem.|[Error](#schemaerror)
500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|[Error](#schemaerror)

### Response Schema

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
anonymous|[[SignatureDevice](#schemasignaturedevice)]|false|No description
» signature_device_id|string|false|unique code usually provided by the device vendor
» device_type|string|false|device type code



<aside class="success">
This operation does not require authentication
</aside>

# Schemas

## OperationSignature

<a name="schemaoperationsignature"></a>

```json
{
  "signature_key": "123455",
  "operation_url": "/accounts/wire-transfer/123455",
  "operation_channel": "MOBILE",
  "status": "NEW",
  "expiration_date": "2017-12-31T23:59:59",
  "signers": [
    {
      "sign_method": 1,
      "sign_status": "PENDING, OK, NOK, LOCKED",
      "sign_completeness_porcentage": 50,
      "signatures": [
        {
          "signature": "{ sign_method: OTP, value: 'GH5T', ... }",
          "status": "OK",
          "signature_date": "2017-12-31T23:59:59"
        }
      ],
      "user_url": "/users/1234567",
      "signant_type": "REQUIRED"
    }
  ]
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
signature_key|string|false|unique key generated by BaaS for this operation signature
operation_url|string|false|URL for the operation in progress
operation_channel|string|false|Channel that initiates the operation
status|string|false|status of the authorization flow
expiration_date|string(date)|false|Expiration date for the signature in ISO 8601 full-format
signers|[[Signer](#schemasigner)]|false|No description
» sign_method|string|true|available sign methods for the current user, like OTP, password, fingerprint, ect
» sign_status|string|true|Status of validation in operation
» sign_completeness_porcentage|integer|true|percentage of sign to complete the authorization of operation
» user_url|string|false|Status of validation in operation
» signant_type|string|false|Defines the required or optional level for this sign
» signatures|[[Signature](#schemasignature)]|false|No description
»» signature|string|false|available sign methods for the current user, like OTP, password, fingerprint, ect
»» status|string|false|One of the following status OK, KO, PENDING, RETRY
»» signature_date|string(date)|false|Signature date



## Signer

<a name="schemasigner"></a>

```json
{
  "sign_method": 1,
  "sign_status": "PENDING, OK, NOK, LOCKED",
  "sign_completeness_porcentage": 50,
  "signatures": [
    {
      "signature": "{ sign_method: OTP, value: 'GH5T', ... }",
      "status": "OK",
      "signature_date": "2017-12-31T23:59:59"
    }
  ],
  "user_url": "/users/1234567",
  "signant_type": "REQUIRED"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
sign_method|string|true|available sign methods for the current user, like OTP, password, fingerprint, ect
sign_status|string|true|Status of validation in operation
sign_completeness_porcentage|integer|true|percentage of sign to complete the authorization of operation
user_url|string|false|Status of validation in operation
signant_type|string|false|Defines the required or optional level for this sign
signatures|[[Signature](#schemasignature)]|false|No description
» signature|string|false|available sign methods for the current user, like OTP, password, fingerprint, ect
» status|string|false|One of the following status OK, KO, PENDING, RETRY
» signature_date|string(date)|false|Signature date



## Signature

<a name="schemasignature"></a>

```json
{
  "signature": "{ sign_method: OTP, value: 'GH5T', ... }",
  "status": "OK",
  "signature_date": "2017-12-31T23:59:59"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
signature|string|false|available sign methods for the current user, like OTP, password, fingerprint, ect
status|string|false|One of the following status OK, KO, PENDING, RETRY
signature_date|string(date)|false|Signature date



## SignatureDevice

<a name="schemasignaturedevice"></a>

```json
{
  "signature_device_id": 1234343,
  "device_type": "TOKEN"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
signature_device_id|string|false|unique code usually provided by the device vendor
device_type|string|false|device type code



## Error

<a name="schemaerror"></a>

```json
{
  "id": "85ca3108-8e11-4ad2-b174-1fc3e5dbef1b",
  "code": "001-001-0001",
  "message": "User or Password Invalid",
  "path": "/CL/v1/customerWebSiteLogin",
  "timestamp": 1482253855188,
  "requestId": "11235f"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
id|string|false|Unique identifier for this specific error instance.  When a fault is encountered in the BaaS service layer, a UUID will be generated for this specific fault, and returned to the client.  It will also be logged to the BaaS log file.  This will enable easier log file correlation and debugging. 
code|string|true|Numeric error code.  The format of this error number should be standardized across all BaaS Services, to clearly indicate the service which has suffered the error, and the cause of this error. Proposed schema  [001-001-0001] [Service Id - Error Category - Error Number] 
message|string|true|Description of the exception
path|string|false|Path of the problematic service call
timestamp|integer(int64)|false|Timestamp of the error
requestId|string|true|Global request id of failed request.  Every request which enters the BaaS platform from the API gateway will have a





