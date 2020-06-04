---
title: AltMarket Exchange API v1
language_tabs:
  - ruby: Ruby
  - python: Python
  - go: Go
  - curl: cURL
  - php: PHP
language_clients:
  - ruby: ""
  - python: ""
  - go: ""
  - curl: ""
  - php: ""
toc_footers: []
includes: []
search: false
highlight_theme: darkula
headingLevel: 2

---

<!-- Generator: Widdershins v4.0.1 -->

<h1 id="altmarket-exchange-api">AltMarket Exchange API v1</h1>

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

# Authentication

* API Key (Cookie)
    - Parameter Name: **Key**, in: header. Your API Key.
    - Parameter Name: **Sign**, in: header. An HMAC signed payload.

Request signing should be performed as indicated in the Python example.

> Code samples

```python
import requests
import datetime
import json
import hashlib
import hmac

test_key = "YOUR_API_KEY"
test_secret = b"YOUR_API_SECRET"

def sign_header(self,secret,payload, is_json):
  if is_json:
    return hmac.new(test_secret, json.dumps(payload).encode('utf-8'), hashlib.sha512).hexdigest().upper()
  else:
    return hmac.new(test_secret, payload.encode('utf-8'), hashlib.sha512).hexdigest().upper()

def header(self,key,secret,payload,is_json=False):
  return {
      'content-type': 'application/json',
      'Key': test_key,
      'Sign': self.sign_header(secret,payload,is_json),
  } 

def timestamp():
  return datetime.datetime.utcnow().isoformat()

payload = "?ts={0}".format(t)
headers = header(test_key,test_secret,payload)
print(headers)
print(payload)

```

<h1 id="altmarket-exchange-api-asset">Asset</h1>

## List Assets

<a id="opIdGetAll"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'content-type' => 'application/json',
  'Key' => 'API_KEY',
  'Sign' => 'API_SIGN'
}

result = RestClient.get 'https://exchange.alt.market/api/assets-info',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'content-type': 'application/json',
  'Key': 'API_KEY',
  'Sign': 'API_SIGN'
}

r = requests.get('https://exchange.alt.market/api/assets-info', headers = headers)

print(r.json())

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "content-type": []string{"application/json"},
        "Key": []string{"API_KEY"},
        "Sign": []string{"API_SIGN"}
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "/api/assets-info", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'content-type' => 'application/json',
    'Key' => 'API_KEY',
    'Sign' => 'API_SIGN'
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://exchange.alt.market/api/assets-info', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

`GET /api/assets-info`

> Example responses

> 200 Response

```
{"data":[{"id":"string","can_deposit":true,"can_withdraw":true,"image_url":"string","asset_name":"string","withdrawal_fee":0,"scale":0}]}
```

```json
{
  "data": [
    {
      "id": "string",
      "can_deposit": true,
      "can_withdraw": true,
      "image_url": "string",
      "asset_name": "string",
      "withdrawal_fee": 0,
      "scale": 0
    }
  ]
}
```

<h3 id="getall-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[AltMarket.Http.Response_1_System.Collections.Generic.IEnumerable_1_AltMarket.Api.AssetResponse_AltMarket_Version_1.0.0.0_Culture_neutral_PublicKeyToken_null_System.Private.CoreLib_Version_4.0.0.0_Culture_neutral_PublicKeyToken_7cec85d7bea7798e_](#schemaqoden.http.response_1_system.collections.generic.ienumerable_1_apilibrary.api.assetresponse_apilibrary_version_1.0.0.0_culture_neutral_publickeytoken_null_system.private.corelib_version_4.0.0.0_culture_neutral_publickeytoken_7cec85d7bea7798e_)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
HMAC Key/Sign
</aside>

<h1 id="altmarket-exchange-api-info">Markets</h1>

## Market Data

<a id="opIdGetInfo"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'content-type' => 'application/json',
  'Key' => 'API_KEY',
  'Sign' => 'API_SIGN'
}

result = RestClient.get 'https://exchange.alt.market/api/markets',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'content-type': 'application/json',
  'Key': 'API_KEY',
  'Sign': 'API_SIGN'
}

r = requests.get('https://exchange.alt.market/api/markets', headers = headers)

print(r.json())

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "content-type": []string{"application/json"},
        "Key": []string{"API_KEY"},
        "Sign": []string{"API_SIGN"}
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "/api/markets", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'content-type' => 'application/json',
    'Key' => 'API_KEY',
    'Sign' => 'API_SIGN'
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://exchange.alt.market/api/markets', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

`GET /api/markets`

> Example responses

> 200 Response

```
{"serverTime":0,"pairs":{"property1":{"baseAsset":"string","quoteAsset":"string","minPrice":0,"maxPrice":0,"minAmount":0,"hidden":0,"fee":0,"makerFee":0,"makerFeeLimit":0,"takerFee":0,"takerFeeLimit":0,"priceScale":0,"amountScale":0,"status":"Open"},"property2":{"baseAsset":"string","quoteAsset":"string","minPrice":0,"maxPrice":0,"minAmount":0,"hidden":0,"fee":0,"makerFee":0,"makerFeeLimit":0,"takerFee":0,"takerFeeLimit":0,"priceScale":0,"amountScale":0,"status":"Open"}},"plaidPublicKey":"string","environment":"string"}
```

```json
{
  "serverTime": 0,
  "pairs": {
    "property1": {
      "baseAsset": "string",
      "quoteAsset": "string",
      "minPrice": 0,
      "maxPrice": 0,
      "minAmount": 0,
      "hidden": 0,
      "fee": 0,
      "makerFee": 0,
      "makerFeeLimit": 0,
      "takerFee": 0,
      "takerFeeLimit": 0,
      "priceScale": 0,
      "amountScale": 0,
      "status": "Open"
    },
    "property2": {
      "baseAsset": "string",
      "quoteAsset": "string",
      "minPrice": 0,
      "maxPrice": 0,
      "minAmount": 0,
      "hidden": 0,
      "fee": 0,
      "makerFee": 0,
      "makerFeeLimit": 0,
      "takerFee": 0,
      "takerFeeLimit": 0,
      "priceScale": 0,
      "amountScale": 0,
      "status": "Open"
    }
  },
  "plaidPublicKey": "string",
  "environment": "string"
}
```

<h3 id="getinfo-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[AltMarket.Api.InfoResponse](#schemaapilibrary.api.inforesponse)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
HMAC Key/Sign
</aside>

<h1 id="altmarket-exchange-api-trade">Trade</h1>

## Create Order

<a id="opIdCreate"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json-patch+json',
  'Accept' => 'text/plain',
  'Cookie' => 'API_KEY'
}

result = RestClient.post 'https://exchange.alt.market/api/order',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json-patch+json',
  'Accept': 'text/plain',
  'Cookie': 'API_KEY'
}

r = requests.post('https://exchange.alt.market/api/order', headers = headers)

print(r.json())

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json-patch+json"},
        "Accept": []string{"text/plain"},
        "Cookie": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "/api/order", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json-patch+json',
    'Accept' => 'text/plain',
    'Cookie' => 'API_KEY',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://exchange.alt.market/api/order', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

`POST /api/order`

> Body parameter

```json
{
  "order": {
    "instrument": "string",
    "type": "string",
    "amount": 0,
    "price": 0,
    "activationPrice": 0,
    "isLimit": true,
    "isStop": true
  }
}
```

<h3 id="create-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[AltMarket.Api.OrderRequest](#schemaapilibrary.api.orderrequest)|false|none|

> Example responses

> 200 Response

```
{"order":{"orderId":"string","total":0,"orderType":"Limit","commission":0,"createdAt":"2020-06-04T09:48:43Z","unitsFilled":0,"isPending":true,"status":"Working","type":"string","amount":0,"price":0,"stopPrice":0,"isLimit":true,"instrument":"string","side":"Buy"}}
```

```json
{
  "order": {
    "orderId": "string",
    "total": 0,
    "orderType": "Limit",
    "commission": 0,
    "createdAt": "2020-06-04T09:48:43Z",
    "unitsFilled": 0,
    "isPending": true,
    "status": "Working",
    "type": "string",
    "amount": 0,
    "price": 0,
    "stopPrice": 0,
    "isLimit": true,
    "instrument": "string",
    "side": "Buy"
  }
}
```

<h3 id="create-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[AltMarket.Api.OrderResponse](#schemaapilibrary.api.orderresponse)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
HMAC Key/Sign
</aside>

## Cancel Order

<a id="opIdCancel"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'content-type' => 'application/json',
  'Key' => 'API_KEY',
  'Sign' => 'API_SIGN'
}

result = RestClient.delete 'https://exchange.alt.market/api/orders/{orderId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'content-type': 'application/json',
  'Key': 'API_KEY',
  'Sign': 'API_SIGN'
}

r = requests.delete('https://exchange.alt.market/api/orders/{orderId}', headers = headers)

print(r.json())

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "content-type": []string{"application/json"},
        "Key": []string{"API_KEY"},
        "Sign": []string{"API_SIGN"}
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("DELETE", "/api/orders/{orderId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'content-type' => 'application/json',
    'Key' => 'API_KEY',
    'Sign' => 'API_SIGN'
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('DELETE','https://exchange.alt.market/api/orders/{orderId}', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

`DELETE /api/orders/{orderId}`

<h3 id="cancel-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|orderId|path|integer(int64)|true|none|

> Example responses

> 200 Response

```
{"order":{"orderId":"string","total":0,"orderType":"Limit","commission":0,"createdAt":"2020-06-04T09:48:43Z","unitsFilled":0,"isPending":true,"status":"Working","type":"string","amount":0,"price":0,"stopPrice":0,"isLimit":true,"instrument":"string","side":"Buy"}}
```

```json
{
  "order": {
    "orderId": "string",
    "total": 0,
    "orderType": "Limit",
    "commission": 0,
    "createdAt": "2020-06-04T09:48:43Z",
    "unitsFilled": 0,
    "isPending": true,
    "status": "Working",
    "type": "string",
    "amount": 0,
    "price": 0,
    "stopPrice": 0,
    "isLimit": true,
    "instrument": "string",
    "side": "Buy"
  }
}
```

<h3 id="cancel-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[AltMarket.Api.OrderResponse](#schemaapilibrary.api.orderresponse)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
HMAC Key/Sign
</aside>

## Open Orders

<a id="opIdMy"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'content-type' => 'application/json',
  'Key' => 'API_KEY',
  'Sign' => 'API_SIGN'
}

result = RestClient.get 'https://exchange.alt.market/api/orders/open',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'content-type': 'application/json',
  'Key': 'API_KEY',
  'Sign': 'API_SIGN'
}

r = requests.get('https://exchange.alt.market/api/orders/open', headers = headers)

print(r.json())

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "content-type": []string{"application/json"},
        "Key": []string{"API_KEY"},
        "Sign": []string{"API_SIGN"}
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "/api/orders/open", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'content-type' => 'application/json',
    'Key' => 'API_KEY',
    'Sign' => 'API_SIGN'
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://exchange.alt.market/api/orders/open', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

`GET /api/orders/open`

> Example responses

> 200 Response

```
[{"orderId":"string","total":0,"orderType":"Limit","commission":0,"createdAt":"2020-06-04T09:48:43Z","unitsFilled":0,"isPending":true,"status":"Working","type":"string","amount":0,"price":0,"stopPrice":0,"isLimit":true,"instrument":"string","side":"Buy"}]
```

```json
[
  {
    "orderId": "string",
    "total": 0,
    "orderType": "Limit",
    "commission": 0,
    "createdAt": "2020-06-04T09:48:43Z",
    "unitsFilled": 0,
    "isPending": true,
    "status": "Working",
    "type": "string",
    "amount": 0,
    "price": 0,
    "stopPrice": 0,
    "isLimit": true,
    "instrument": "string",
    "side": "Buy"
  }
]
```

<h3 id="my-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|

<h3 id="my-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[AltMarket.Api.OrderInfoResponse](#schemaapilibrary.api.orderinforesponse)]|false|none|none|
|» orderId|string|false|none|none|
|» total|number(double)|false|none|none|
|» orderType|string|false|none|none|
|» commission|number(double)|false|none|none|
|» createdAt|string(date-time)|false|none|none|
|» unitsFilled|number(double)|false|none|none|
|» isPending|boolean|false|none|none|
|» status|string|false|none|none|
|» type|string|false|none|none|
|» amount|number(double)|false|none|none|
|» price|number(double)|false|none|none|
|» stopPrice|number(double)|false|none|none|
|» isLimit|boolean|false|none|none|
|» instrument|string|false|none|none|
|» side|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|orderType|Limit|
|orderType|Market|
|orderType|StopLimit|
|orderType|StopMarket|
|status|Working|
|status|Rejected|
|status|Cancelled|
|status|Completed|
|side|Buy|
|side|Sell|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
HMAC Key/Sign
</aside>

## Cancel All Active Orders

<a id="opIdCancelAllActiveOrders"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'content-type' => 'application/json',
  'Key' => 'API_KEY',
  'Sign' => 'API_SIGN'
}

result = RestClient.delete 'https://exchange.alt.market/api/orders',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'content-type': 'application/json',
  'Key': 'API_KEY',
  'Sign': 'API_SIGN'
}

r = requests.delete('https://exchange.alt.market/api/orders', headers = headers)

print(r.json())

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "content-type": []string{"application/json"},
        "Key": []string{"API_KEY"},
        "Sign": []string{"API_SIGN"}
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("DELETE", "/api/orders", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'content-type' => 'application/json',
    'Key' => 'API_KEY',
    'Sign' => 'API_SIGN'
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('DELETE','https://exchange.alt.market/api/orders', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

`DELETE /api/orders`

> Example responses

> 200 Response

```
{"data":0}
```

```json
{
  "data": 0
}
```

<h3 id="cancelallactiveorders-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[AltMarket.Http.Response_1_System.Int32_System.Private.CoreLib_Version_4.0.0.0_Culture_neutral_PublicKeyToken_7cec85d7bea7798e_](#schemaqoden.http.response_1_system.int32_system.private.corelib_version_4.0.0.0_culture_neutral_publickeytoken_7cec85d7bea7798e_)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
HMAC Key/Sign
</aside>

## Order History

<a id="opIdOrderHistory"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'content-type' => 'application/json',
  'Key' => 'API_KEY',
  'Sign' => 'API_SIGN'
}

result = RestClient.get 'https://exchange.alt.market/api/order_history',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'content-type': 'application/json',
  'Key': 'API_KEY',
  'Sign': 'API_SIGN'
}

r = requests.get('https://exchange.alt.market/api/order_history', headers = headers)

print(r.json())

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "content-type": []string{"application/json"},
        "Key": []string{"API_KEY"},
        "Sign": []string{"API_SIGN"}
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "/api/order_history", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'content-type' => 'application/json',
    'Key' => 'API_KEY',
    'Sign' => 'API_SIGN'
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://exchange.alt.market/api/order_history', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

`GET /api/order_history`

<h3 id="orderhistory-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|Market|query|string|false|none|
|Side|query|string|false|none|
|StartDate|query|string(date-time)|false|none|
|EndDate|query|string(date-time)|false|none|
|AscOrder|query|array[string]|false|none|
|DescOrder|query|array[string]|false|none|
|IsHideCanceled|query|boolean|false|none|
|Page|query|integer(int32)|false|none|
|PerPage|query|integer(int32)|false|none|

#### Enumerated Values

|Parameter|Value|
|---|---|
|Side|Buy|
|Side|Sell|

> Example responses

> 200 Response

```
{"filters":{},"paging":{"page":0,"per_page":0,"total":0},"data":[{"orderId":"string","total":0,"orderType":"Limit","commission":0,"createdAt":"2020-06-04T09:48:43Z","unitsFilled":0,"isPending":true,"status":"Working","type":"string","amount":0,"price":0,"stopPrice":0,"isLimit":true,"instrument":"string","side":"Buy"}]}
```

```json
{
  "filters": {},
  "paging": {
    "page": 0,
    "per_page": 0,
    "total": 0
  },
  "data": [
    {
      "orderId": "string",
      "total": 0,
      "orderType": "Limit",
      "commission": 0,
      "createdAt": "2020-06-04T09:48:43Z",
      "unitsFilled": 0,
      "isPending": true,
      "status": "Working",
      "type": "string",
      "amount": 0,
      "price": 0,
      "stopPrice": 0,
      "isLimit": true,
      "instrument": "string",
      "side": "Buy"
    }
  ]
}
```

<h3 id="orderhistory-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[AltMarket.Http.FilteredResponse_1_AltMarket.Api.OrderInfoResponse_AltMarket_Version_1.0.0.0_Culture_neutral_PublicKeyToken_null_](#schemaqoden.http.filteredresponse_1_apilibrary.api.orderinforesponse_apilibrary_version_1.0.0.0_culture_neutral_publickeytoken_null_)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
HMAC Key/Sign
</aside>

## Get Trade History 

<a id="opIdGetTradeHistoryAsync"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'content-type' => 'application/json',
  'Key' => 'API_KEY',
  'Sign' => 'API_SIGN'
}

result = RestClient.get 'https://exchange.alt.market/api/trade_history',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'content-type': 'application/json',
  'Key': 'API_KEY',
  'Sign': 'API_SIGN'
}

r = requests.get('https://exchange.alt.market/api/trade_history', headers = headers)

print(r.json())

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "content-type": []string{"application/json"},
        "Key": []string{"API_KEY"},
        "Sign": []string{"API_SIGN"}
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "/api/trade_history", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'content-type' => 'application/json',
    'Key' => 'API_KEY',
    'Sign' => 'API_SIGN'
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://exchange.alt.market/api/trade_history', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

`GET /api/trade_history`

<h3 id="gettradehistoryasync-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|Market|query|string|false|none|
|Side|query|string|false|none|
|StartDate|query|string(date-time)|false|none|
|EndDate|query|string(date-time)|false|none|
|AscOrder|query|array[string]|false|none|
|DescOrder|query|array[string]|false|none|
|Page|query|integer(int32)|false|none|
|PerPage|query|integer(int32)|false|none|

#### Enumerated Values

|Parameter|Value|
|---|---|
|Side|Buy|
|Side|Sell|

> Example responses

> 200 Response

```
{"filters":{},"paging":{"page":0,"per_page":0,"total":0},"data":[{"tradeSeq":0,"tradeTime":"2020-06-04T09:48:43Z","amount":0,"executionPrice":0,"instrument":"string","side":"Buy","commission":0}]}
```

```json
{
  "filters": {},
  "paging": {
    "page": 0,
    "per_page": 0,
    "total": 0
  },
  "data": [
    {
      "tradeSeq": 0,
      "tradeTime": "2020-06-04T09:48:43Z",
      "amount": 0,
      "executionPrice": 0,
      "instrument": "string",
      "side": "Buy",
      "commission": 0
    }
  ]
}
```

<h3 id="gettradehistoryasync-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[AltMarket.Http.FilteredResponse_1_AltMarket.Account.TradeHistoryItem_AltMarket.Account.Data_Version_1.0.0.0_Culture_neutral_PublicKeyToken_null_](#schemaqoden.http.filteredresponse_1_qodex.account.tradehistoryitem_qodex.account.data_version_1.0.0.0_culture_neutral_publickeytoken_null_)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
HMAC Key/Sign
</aside>

<h1 id="altmarket-exchange-api-wallet">Wallet</h1>

## Get Deposit Address

<a id="opIdRequestFundsDeposit"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json-patch+json',
  'Accept' => 'text/plain',
  'Cookie' => 'API_KEY'
}

result = RestClient.post 'https://exchange.alt.market/api/wallet/deposit',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json-patch+json',
  'Accept': 'text/plain',
  'Cookie': 'API_KEY'
}

r = requests.post('https://exchange.alt.market/api/wallet/deposit', headers = headers)

print(r.json())

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json-patch+json"},
        "Accept": []string{"text/plain"},
        "Cookie": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "/api/wallet/deposit", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json-patch+json',
    'Accept' => 'text/plain',
    'Cookie' => 'API_KEY',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://exchange.alt.market/api/wallet/deposit', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

`POST /api/wallet/deposit`

> Body parameter

```json
{
  "assetId": "string"
}
```

<h3 id="requestfundsdeposit-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[AltMarket.FrontOffice.DepositFundsRequest](#schemamyexchange.frontoffice.depositfundsrequest)|false|none|

> Example responses

> 200 Response

```
{"asset":"string","paymentSystem":"string","address":"string","error":"string"}
```

```json
{
  "asset": "string",
  "paymentSystem": "string",
  "address": "string",
  "error": "string"
}
```

<h3 id="requestfundsdeposit-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[AltMarket.FrontOffice.DepositFundsResponse](#schemamyexchange.frontoffice.depositfundsresponse)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
HMAC Key/Sign
</aside>

## Withdrawal

<a id="opIdWithdrawal"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json-patch+json',
  'Accept' => 'text/plain',
  'Cookie' => 'API_KEY'
}

result = RestClient.post 'https://exchange.alt.market/api/wallet/withdrawal',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json-patch+json',
  'Accept': 'text/plain',
  'Cookie': 'API_KEY'
}

r = requests.post('https://exchange.alt.market/api/wallet/withdrawal', headers = headers)

print(r.json())

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json-patch+json"},
        "Accept": []string{"text/plain"},
        "Cookie": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "/api/wallet/withdrawal", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json-patch+json',
    'Accept' => 'text/plain',
    'Cookie' => 'API_KEY',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://exchange.alt.market/api/wallet/withdrawal', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

`POST /api/wallet/withdrawal`

> Body parameter

```json
{
  "transferId": "string",
  "assetId": "string",
  "amount": 0,
  "address": "string"
}
```

<h3 id="withdrawal-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[AltMarket.Api.WithdrawalRequest](#schemaapilibrary.api.withdrawalrequest)|false|none|

> Example responses

> 200 Response

```
{"asset":"string","paymentSystem":"string","transferId":"string","type":"Deposit","status":"AwaitingConfirmation","amount":"string","fee":"string","errorDetails":"string","createdAt":"2020-06-04T09:48:43Z","updatedAt":"2020-06-04T09:48:43Z","txId":"string","blockchainLink":"string","errorCode":"string","confirmations":0,"confirmationsRequired":0,"targetAddress":"string"}
```

```json
{
  "asset": "string",
  "paymentSystem": "string",
  "transferId": "string",
  "type": "Deposit",
  "status": "AwaitingConfirmation",
  "amount": "string",
  "fee": "string",
  "errorDetails": "string",
  "createdAt": "2020-06-04T09:48:43Z",
  "updatedAt": "2020-06-04T09:48:43Z",
  "txId": "string",
  "blockchainLink": "string",
  "errorCode": "string",
  "confirmations": 0,
  "confirmationsRequired": 0,
  "targetAddress": "string"
}
```

<h3 id="withdrawal-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[AltMarket.Account.TransferData](#schemaqodex.account.transferdata)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
HMAC Key/Sign
</aside>

## Transfer History 

<a id="opIdGetTransfers"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'content-type' => 'application/json',
  'Key' => 'API_KEY',
  'Sign' => 'API_SIGN'
}

result = RestClient.get 'https://exchange.alt.market/api/wallet/transfers',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'content-type': 'application/json',
  'Key': 'API_KEY',
  'Sign': 'API_SIGN'
}

r = requests.get('https://exchange.alt.market/api/wallet/transfers', headers = headers)

print(r.json())

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "content-type": []string{"application/json"},
        "Key": []string{"API_KEY"},
        "Sign": []string{"API_SIGN"}
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "/api/wallet/transfers", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'content-type' => 'application/json',
    'Key' => 'API_KEY',
    'Sign' => 'API_SIGN'
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://exchange.alt.market/api/wallet/transfers', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

`GET /api/wallet/transfers`

<h3 id="gettransfers-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|count|query|integer(int32)|false|none|

> Example responses

> 200 Response

```
[{"asset":"string","paymentSystem":"string","transferId":"string","type":"Deposit","status":"AwaitingConfirmation","amount":"string","fee":"string","errorDetails":"string","createdAt":"2020-06-04T09:48:43Z","updatedAt":"2020-06-04T09:48:43Z","txId":"string","blockchainLink":"string","errorCode":"string","confirmations":0,"confirmationsRequired":0,"targetAddress":"string"}]
```

```json
[
  {
    "asset": "string",
    "paymentSystem": "string",
    "transferId": "string",
    "type": "Deposit",
    "status": "AwaitingConfirmation",
    "amount": "string",
    "fee": "string",
    "errorDetails": "string",
    "createdAt": "2020-06-04T09:48:43Z",
    "updatedAt": "2020-06-04T09:48:43Z",
    "txId": "string",
    "blockchainLink": "string",
    "errorCode": "string",
    "confirmations": 0,
    "confirmationsRequired": 0,
    "targetAddress": "string"
  }
]
```

<h3 id="gettransfers-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|

<h3 id="gettransfers-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[AltMarket.Account.TransferData](#schemaqodex.account.transferdata)]|false|none|none|
|» asset|string|false|none|none|
|» paymentSystem|string|false|none|none|
|» transferId|string|false|none|none|
|» type|string|false|none|none|
|» status|string|false|none|none|
|» amount|string|false|none|none|
|» fee|string|false|none|none|
|» errorDetails|string|false|none|none|
|» createdAt|string(date-time)|false|none|none|
|» updatedAt|string(date-time)|false|none|none|
|» txId|string|false|none|none|
|» blockchainLink|string|false|none|none|
|» errorCode|string|false|none|none|
|» confirmations|integer(int32)|false|none|none|
|» confirmationsRequired|integer(int32)|false|none|none|
|» targetAddress|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|Deposit|
|type|Withdrawal|
|status|AwaitingConfirmation|
|status|Unused_Pending|
|status|Completed|
|status|Failed|
|status|Unused_PendingCancellation|
|status|Unused_Canceled|
|status|Unused_CompletedUpdate|
|status|Unused_FundsLocked|
|status|Unused_PaymentSystemError|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
HMAC Key/Sign
</aside>

## Balance

<a id="opIdFullAssets"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'content-type' => 'application/json',
  'Key' => 'API_KEY',
  'Sign' => 'API_SIGN'
}

result = RestClient.get 'https://exchange.alt.market/api/wallet/balance',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'content-type': 'application/json',
  'Key': 'API_KEY',
  'Sign': 'API_SIGN'
}

r = requests.get('https://exchange.alt.market/api/wallet/balance', headers = headers)

print(r.json())

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "content-type": []string{"application/json"},
        "Key": []string{"API_KEY"},
        "Sign": []string{"API_SIGN"}
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "/api/wallet/balance", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'content-type' => 'application/json',
    'Key' => 'API_KEY',
    'Sign' => 'API_SIGN'
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://exchange.alt.market/api/wallet/balance', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

`GET /api/wallet/balance`

> Example responses

> 200 Response

```
[{"asset":"string","totalBalance":0,"inOrder":0,"availableBalance":0}]
```

```json
[
  {
    "asset": "string",
    "totalBalance": 0,
    "inOrder": 0,
    "availableBalance": 0
  }
]
```

<h3 id="fullassets-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|

<h3 id="fullassets-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[AltMarket.Api.AccountAssetResponse](#schemaapilibrary.api.accountassetresponse)]|false|none|none|
|» asset|string|false|none|none|
|» totalBalance|number(double)|false|none|none|
|» inOrder|number(double)|false|none|none|
|» availableBalance|number(double)|false|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
HMAC Key/Sign
</aside>

# Schemas

<h2 id="tocS_AltMarket.Api.AssetResponse">AltMarket.Api.AssetResponse</h2>

<a id="schemaapilibrary.api.assetresponse"></a>
<a id="schema_AltMarket.Api.AssetResponse"></a>
<a id="tocSapilibrary.api.assetresponse"></a>
<a id="tocsapilibrary.api.assetresponse"></a>

```json
{
  "id": "string",
  "can_deposit": true,
  "can_withdraw": true,
  "image_url": "string",
  "asset_name": "string",
  "withdrawal_fee": 0,
  "scale": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|none|
|can_deposit|boolean|false|none|none|
|can_withdraw|boolean|false|none|none|
|image_url|string|false|none|none|
|asset_name|string|false|none|none|
|withdrawal_fee|number(double)|false|none|none|
|scale|integer(int32)|false|none|none|

<h2 id="tocS_AltMarket.Api.InfoResponse">AltMarket.Api.InfoResponse</h2>

<a id="schemaapilibrary.api.inforesponse"></a>
<a id="schema_AltMarket.Api.InfoResponse"></a>
<a id="tocSapilibrary.api.inforesponse"></a>
<a id="tocsapilibrary.api.inforesponse"></a>

```json
{
  "serverTime": 0,
  "pairs": {
    "property1": {
      "baseAsset": "string",
      "quoteAsset": "string",
      "minPrice": 0,
      "maxPrice": 0,
      "minAmount": 0,
      "hidden": 0,
      "fee": 0,
      "makerFee": 0,
      "makerFeeLimit": 0,
      "takerFee": 0,
      "takerFeeLimit": 0,
      "priceScale": 0,
      "amountScale": 0,
      "status": "Open"
    },
    "property2": {
      "baseAsset": "string",
      "quoteAsset": "string",
      "minPrice": 0,
      "maxPrice": 0,
      "minAmount": 0,
      "hidden": 0,
      "fee": 0,
      "makerFee": 0,
      "makerFeeLimit": 0,
      "takerFee": 0,
      "takerFeeLimit": 0,
      "priceScale": 0,
      "amountScale": 0,
      "status": "Open"
    }
  },
  "plaidPublicKey": "string",
  "environment": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|serverTime|integer(int64)|false|none|none|
|pairs|object|false|none|none|
|» **additionalProperties**|[AltMarket.Api.MarketInfo](#schemaapilibrary.api.marketinfo)|false|none|none|
|plaidPublicKey|string|false|none|none|
|environment|string|false|none|none|

<h2 id="tocS_AltMarket.Api.MarketInfo">AltMarket.Api.MarketInfo</h2>

<a id="schemaapilibrary.api.marketinfo"></a>
<a id="schema_AltMarket.Api.MarketInfo"></a>
<a id="tocSapilibrary.api.marketinfo"></a>
<a id="tocsapilibrary.api.marketinfo"></a>

```json
{
  "baseAsset": "string",
  "quoteAsset": "string",
  "minPrice": 0,
  "maxPrice": 0,
  "minAmount": 0,
  "hidden": 0,
  "fee": 0,
  "makerFee": 0,
  "makerFeeLimit": 0,
  "takerFee": 0,
  "takerFeeLimit": 0,
  "priceScale": 0,
  "amountScale": 0,
  "status": "Open"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|baseAsset|string|false|none|none|
|quoteAsset|string|false|none|none|
|minPrice|number(double)|false|none|none|
|maxPrice|number(double)|false|none|none|
|minAmount|number(double)|false|none|none|
|hidden|integer(int32)|false|none|none|
|fee|number(double)|false|none|none|
|makerFee|number(double)|false|none|none|
|makerFeeLimit|number(double)|false|none|none|
|takerFee|number(double)|false|none|none|
|takerFeeLimit|number(double)|false|none|none|
|priceScale|integer(int32)|false|none|none|
|amountScale|integer(int32)|false|none|none|
|status|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|status|Open|
|status|Halted|
|status|Paused|

<h2 id="tocS_AltMarket.Api.OrderRequest">AltMarket.Api.OrderRequest</h2>

<a id="schemaapilibrary.api.orderrequest"></a>
<a id="schema_AltMarket.Api.OrderRequest"></a>
<a id="tocSapilibrary.api.orderrequest"></a>
<a id="tocsapilibrary.api.orderrequest"></a>

```json
{
  "order": {
    "instrument": "string",
    "type": "string",
    "amount": 0,
    "price": 0,
    "activationPrice": 0,
    "isLimit": true,
    "isStop": true,
    "side": "Buy",
    "orderType": "Limit"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|order|[AltMarket.Api.OrderInfoRequest](#schemaapilibrary.api.orderinforequest)|false|none|none|

<h2 id="tocS_AltMarket.Api.OrderInfoRequest">AltMarket.Api.OrderInfoRequest</h2>

<a id="schemaapilibrary.api.orderinforequest"></a>
<a id="schema_AltMarket.Api.OrderInfoRequest"></a>
<a id="tocSapilibrary.api.orderinforequest"></a>
<a id="tocsapilibrary.api.orderinforequest"></a>

```json
{
  "instrument": "string",
  "type": "string",
  "amount": 0,
  "price": 0,
  "activationPrice": 0,
  "isLimit": true,
  "isStop": true,
  "side": "Buy",
  "orderType": "Limit"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|instrument|string|false|none|none|
|type|string|false|none|none|
|amount|number(double)|false|none|none|
|price|number(double)|false|none|none|
|activationPrice|number(double)|false|none|none|
|isLimit|boolean|false|none|none|
|isStop|boolean|false|none|none|
|side|string|false|read-only|none|
|orderType|string|false|read-only|none|

#### Enumerated Values

|Property|Value|
|---|---|
|side|Buy|
|side|Sell|
|orderType|Limit|
|orderType|Market|
|orderType|StopLimit|
|orderType|StopMarket|

<h2 id="tocS_AltMarket.Api.OrderResponse">AltMarket.Api.OrderResponse</h2>

<a id="schemaapilibrary.api.orderresponse"></a>
<a id="schema_AltMarket.Api.OrderResponse"></a>
<a id="tocSapilibrary.api.orderresponse"></a>
<a id="tocsapilibrary.api.orderresponse"></a>

```json
{
  "order": {
    "orderId": "string",
    "total": 0,
    "orderType": "Limit",
    "commission": 0,
    "createdAt": "2020-06-04T09:48:43Z",
    "unitsFilled": 0,
    "isPending": true,
    "status": "Working",
    "type": "string",
    "amount": 0,
    "price": 0,
    "stopPrice": 0,
    "isLimit": true,
    "instrument": "string",
    "side": "Buy"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|order|[AltMarket.Api.OrderInfoResponse](#schemaapilibrary.api.orderinforesponse)|false|none|none|

<h2 id="tocS_AltMarket.Api.OrderInfoResponse">AltMarket.Api.OrderInfoResponse</h2>

<a id="schemaapilibrary.api.orderinforesponse"></a>
<a id="schema_AltMarket.Api.OrderInfoResponse"></a>
<a id="tocSapilibrary.api.orderinforesponse"></a>
<a id="tocsapilibrary.api.orderinforesponse"></a>

```json
{
  "orderId": "string",
  "total": 0,
  "orderType": "Limit",
  "commission": 0,
  "createdAt": "2020-06-04T09:48:43Z",
  "unitsFilled": 0,
  "isPending": true,
  "status": "Working",
  "type": "string",
  "amount": 0,
  "price": 0,
  "stopPrice": 0,
  "isLimit": true,
  "instrument": "string",
  "side": "Buy"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|orderId|string|false|none|none|
|total|number(double)|false|none|none|
|orderType|string|false|none|none|
|commission|number(double)|false|none|none|
|createdAt|string(date-time)|false|none|none|
|unitsFilled|number(double)|false|none|none|
|isPending|boolean|false|none|none|
|status|string|false|none|none|
|type|string|false|none|none|
|amount|number(double)|false|none|none|
|price|number(double)|false|none|none|
|stopPrice|number(double)|false|none|none|
|isLimit|boolean|false|none|none|
|instrument|string|false|none|none|
|side|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|orderType|Limit|
|orderType|Market|
|orderType|StopLimit|
|orderType|StopMarket|
|status|Working|
|status|Rejected|
|status|Cancelled|
|status|Completed|
|side|Buy|
|side|Sell|

<h2 id="tocS_AltMarket.Http.Paging">AltMarket.Http.Paging</h2>

<a id="schemaqoden.http.paging"></a>
<a id="schema_AltMarket.Http.Paging"></a>
<a id="tocSqoden.http.paging"></a>
<a id="tocsqoden.http.paging"></a>

```json
{
  "page": 0,
  "per_page": 0,
  "total": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|page|integer(int32)|false|none|none|
|per_page|integer(int32)|false|none|none|
|total|integer(int32)|false|none|none|

<h2 id="tocS_AltMarket.Account.TradeHistoryItem">AltMarket.Account.TradeHistoryItem</h2>

<a id="schemaqodex.account.tradehistoryitem"></a>
<a id="schema_AltMarket.Account.TradeHistoryItem"></a>
<a id="tocSqodex.account.tradehistoryitem"></a>
<a id="tocsqodex.account.tradehistoryitem"></a>

```json
{
  "tradeSeq": 0,
  "tradeTime": "2020-06-04T09:48:43Z",
  "amount": 0,
  "executionPrice": 0,
  "instrument": "string",
  "side": "Buy",
  "commission": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|tradeSeq|integer(int64)|false|none|none|
|tradeTime|string(date-time)|false|none|none|
|amount|number(double)|false|none|none|
|executionPrice|number(double)|false|none|none|
|instrument|string|false|none|none|
|side|string|false|none|none|
|commission|number(double)|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|side|Buy|
|side|Sell|

<h2 id="tocS_AltMarket.FrontOffice.DepositFundsRequest">AltMarket.FrontOffice.DepositFundsRequest</h2>

<a id="schemamyexchange.frontoffice.depositfundsrequest"></a>
<a id="schema_AltMarket.FrontOffice.DepositFundsRequest"></a>
<a id="tocSmyexchange.frontoffice.depositfundsrequest"></a>
<a id="tocsmyexchange.frontoffice.depositfundsrequest"></a>

```json
{
  "assetId": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|assetId|string|false|none|none|

<h2 id="tocS_AltMarket.FrontOffice.DepositFundsResponse">AltMarket.FrontOffice.DepositFundsResponse</h2>

<a id="schemamyexchange.frontoffice.depositfundsresponse"></a>
<a id="schema_AltMarket.FrontOffice.DepositFundsResponse"></a>
<a id="tocSmyexchange.frontoffice.depositfundsresponse"></a>
<a id="tocsmyexchange.frontoffice.depositfundsresponse"></a>

```json
{
  "asset": "string",
  "paymentSystem": "string",
  "address": "string",
  "error": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|asset|string|false|none|none|
|paymentSystem|string|false|none|none|
|address|string|false|none|none|
|error|string|false|none|none|

<h2 id="tocS_AltMarket.Api.WithdrawalRequest">AltMarket.Api.WithdrawalRequest</h2>

<a id="schemaapilibrary.api.withdrawalrequest"></a>
<a id="schema_AltMarket.Api.WithdrawalRequest"></a>
<a id="tocSapilibrary.api.withdrawalrequest"></a>
<a id="tocsapilibrary.api.withdrawalrequest"></a>

```json
{
  "transferId": "string",
  "assetId": "string",
  "amount": 0,
  "address": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|transferId|string|false|none|none|
|assetId|string|false|none|none|
|amount|number(double)|false|none|none|
|address|string|false|none|none|

<h2 id="tocS_AltMarket.Account.TransferData">AltMarket.Account.TransferData</h2>

<a id="schemaqodex.account.transferdata"></a>
<a id="schema_AltMarket.Account.TransferData"></a>
<a id="tocSqodex.account.transferdata"></a>
<a id="tocsqodex.account.transferdata"></a>

```json
{
  "asset": "string",
  "paymentSystem": "string",
  "transferId": "string",
  "type": "Deposit",
  "status": "AwaitingConfirmation",
  "amount": "string",
  "fee": "string",
  "errorDetails": "string",
  "createdAt": "2020-06-04T09:48:43Z",
  "updatedAt": "2020-06-04T09:48:43Z",
  "txId": "string",
  "blockchainLink": "string",
  "errorCode": "string",
  "confirmations": 0,
  "confirmationsRequired": 0,
  "targetAddress": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|asset|string|false|none|none|
|paymentSystem|string|false|none|none|
|transferId|string|false|none|none|
|type|string|false|none|none|
|status|string|false|none|none|
|amount|string|false|none|none|
|fee|string|false|none|none|
|errorDetails|string|false|none|none|
|createdAt|string(date-time)|false|none|none|
|updatedAt|string(date-time)|false|none|none|
|txId|string|false|none|none|
|blockchainLink|string|false|none|none|
|errorCode|string|false|none|none|
|confirmations|integer(int32)|false|none|none|
|confirmationsRequired|integer(int32)|false|none|none|
|targetAddress|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|Deposit|
|type|Withdrawal|
|status|AwaitingConfirmation|
|status|Unused_Pending|
|status|Completed|
|status|Failed|
|status|Unused_PendingCancellation|
|status|Unused_Canceled|
|status|Unused_CompletedUpdate|
|status|Unused_FundsLocked|
|status|Unused_PaymentSystemError|

<h2 id="tocS_AltMarket.Api.AccountAssetResponse">AltMarket.Api.AccountAssetResponse</h2>

<a id="schemaapilibrary.api.accountassetresponse"></a>
<a id="schema_AltMarket.Api.AccountAssetResponse"></a>
<a id="tocSapilibrary.api.accountassetresponse"></a>
<a id="tocsapilibrary.api.accountassetresponse"></a>

```json
{
  "asset": "string",
  "totalBalance": 0,
  "inOrder": 0,
  "availableBalance": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|asset|string|false|none|none|
|totalBalance|number(double)|false|none|none|
|inOrder|number(double)|false|none|none|
|availableBalance|number(double)|false|none|none|

<h2 id="tocS_AltMarket.Http.Response_1_System.Collections.Generic.IEnumerable_1_AltMarket.Api.AssetResponse_AltMarket_Version_1.0.0.0_Culture_neutral_PublicKeyToken_null_System.Private.CoreLib_Version_4.0.0.0_Culture_neutral_PublicKeyToken_7cec85d7bea7798e_">AltMarket.Http.Response_1_System.Collections.Generic.IEnumerable_1_AltMarket.Api.AssetResponse_AltMarket_Version_1.0.0.0_Culture_neutral_PublicKeyToken_null_System.Private.CoreLib_Version_4.0.0.0_Culture_neutral_PublicKeyToken_7cec85d7bea7798e_</h2>

<a id="schemaqoden.http.response_1_system.collections.generic.ienumerable_1_apilibrary.api.assetresponse_apilibrary_version_1.0.0.0_culture_neutral_publickeytoken_null_system.private.corelib_version_4.0.0.0_culture_neutral_publickeytoken_7cec85d7bea7798e_"></a>
<a id="schema_AltMarket.Http.Response_1_System.Collections.Generic.IEnumerable_1_AltMarket.Api.AssetResponse_AltMarket_Version_1.0.0.0_Culture_neutral_PublicKeyToken_null_System.Private.CoreLib_Version_4.0.0.0_Culture_neutral_PublicKeyToken_7cec85d7bea7798e_"></a>
<a id="tocSqoden.http.response_1_system.collections.generic.ienumerable_1_apilibrary.api.assetresponse_apilibrary_version_1.0.0.0_culture_neutral_publickeytoken_null_system.private.corelib_version_4.0.0.0_culture_neutral_publickeytoken_7cec85d7bea7798e_"></a>
<a id="tocsqoden.http.response_1_system.collections.generic.ienumerable_1_apilibrary.api.assetresponse_apilibrary_version_1.0.0.0_culture_neutral_publickeytoken_null_system.private.corelib_version_4.0.0.0_culture_neutral_publickeytoken_7cec85d7bea7798e_"></a>

```json
{
  "data": [
    {
      "id": "string",
      "can_deposit": true,
      "can_withdraw": true,
      "image_url": "string",
      "asset_name": "string",
      "withdrawal_fee": 0,
      "scale": 0
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|data|[[AltMarket.Api.AssetResponse](#schemaapilibrary.api.assetresponse)]|false|none|none|

<h2 id="tocS_AltMarket.Http.Response_1_System.Int32_System.Private.CoreLib_Version_4.0.0.0_Culture_neutral_PublicKeyToken_7cec85d7bea7798e_">AltMarket.Http.Response_1_System.Int32_System.Private.CoreLib_Version_4.0.0.0_Culture_neutral_PublicKeyToken_7cec85d7bea7798e_</h2>

<a id="schemaqoden.http.response_1_system.int32_system.private.corelib_version_4.0.0.0_culture_neutral_publickeytoken_7cec85d7bea7798e_"></a>
<a id="schema_AltMarket.Http.Response_1_System.Int32_System.Private.CoreLib_Version_4.0.0.0_Culture_neutral_PublicKeyToken_7cec85d7bea7798e_"></a>
<a id="tocSqoden.http.response_1_system.int32_system.private.corelib_version_4.0.0.0_culture_neutral_publickeytoken_7cec85d7bea7798e_"></a>
<a id="tocsqoden.http.response_1_system.int32_system.private.corelib_version_4.0.0.0_culture_neutral_publickeytoken_7cec85d7bea7798e_"></a>

```json
{
  "data": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|data|integer(int32)|false|none|none|

<h2 id="tocS_AltMarket.Http.FilteredResponse_1_AltMarket.Api.OrderInfoResponse_AltMarket_Version_1.0.0.0_Culture_neutral_PublicKeyToken_null_">AltMarket.Http.FilteredResponse_1_AltMarket.Api.OrderInfoResponse_AltMarket_Version_1.0.0.0_Culture_neutral_PublicKeyToken_null_</h2>

<a id="schemaqoden.http.filteredresponse_1_apilibrary.api.orderinforesponse_apilibrary_version_1.0.0.0_culture_neutral_publickeytoken_null_"></a>
<a id="schema_AltMarket.Http.FilteredResponse_1_AltMarket.Api.OrderInfoResponse_AltMarket_Version_1.0.0.0_Culture_neutral_PublicKeyToken_null_"></a>
<a id="tocSqoden.http.filteredresponse_1_apilibrary.api.orderinforesponse_apilibrary_version_1.0.0.0_culture_neutral_publickeytoken_null_"></a>
<a id="tocsqoden.http.filteredresponse_1_apilibrary.api.orderinforesponse_apilibrary_version_1.0.0.0_culture_neutral_publickeytoken_null_"></a>

```json
{
  "filters": {},
  "paging": {
    "page": 0,
    "per_page": 0,
    "total": 0
  },
  "data": [
    {
      "orderId": "string",
      "total": 0,
      "orderType": "Limit",
      "commission": 0,
      "createdAt": "2020-06-04T09:48:43Z",
      "unitsFilled": 0,
      "isPending": true,
      "status": "Working",
      "type": "string",
      "amount": 0,
      "price": 0,
      "stopPrice": 0,
      "isLimit": true,
      "instrument": "string",
      "side": "Buy"
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|filters|object|false|none|none|
|paging|[AltMarket.Http.Paging](#schemaqoden.http.paging)|false|none|none|
|data|[[AltMarket.Api.OrderInfoResponse](#schemaapilibrary.api.orderinforesponse)]|false|none|none|

<h2 id="tocS_AltMarket.Http.FilteredResponse_1_AltMarket.Account.TradeHistoryItem_AltMarket.Account.Data_Version_1.0.0.0_Culture_neutral_PublicKeyToken_null_">AltMarket.Http.FilteredResponse_1_AltMarket.Account.TradeHistoryItem_AltMarket.Account.Data_Version_1.0.0.0_Culture_neutral_PublicKeyToken_null_</h2>

<a id="schemaqoden.http.filteredresponse_1_qodex.account.tradehistoryitem_qodex.account.data_version_1.0.0.0_culture_neutral_publickeytoken_null_"></a>
<a id="schema_AltMarket.Http.FilteredResponse_1_AltMarket.Account.TradeHistoryItem_AltMarket.Account.Data_Version_1.0.0.0_Culture_neutral_PublicKeyToken_null_"></a>
<a id="tocSqoden.http.filteredresponse_1_qodex.account.tradehistoryitem_qodex.account.data_version_1.0.0.0_culture_neutral_publickeytoken_null_"></a>
<a id="tocsqoden.http.filteredresponse_1_qodex.account.tradehistoryitem_qodex.account.data_version_1.0.0.0_culture_neutral_publickeytoken_null_"></a>

```json
{
  "filters": {},
  "paging": {
    "page": 0,
    "per_page": 0,
    "total": 0
  },
  "data": [
    {
      "tradeSeq": 0,
      "tradeTime": "2020-06-04T09:48:43Z",
      "amount": 0,
      "executionPrice": 0,
      "instrument": "string",
      "side": "Buy",
      "commission": 0
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|filters|object|false|none|none|
|paging|[AltMarket.Http.Paging](#schemaqoden.http.paging)|false|none|none|
|data|[[AltMarket.Account.TradeHistoryItem](#schemaqodex.account.tradehistoryitem)]|false|none|none|

