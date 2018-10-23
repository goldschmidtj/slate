---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Vandelay Industries API! You can use our API to access manufacturing API endpoints, which can get information on various factories, machines, warehouses and inventory items in our database.

We have language bindings in Shell, Ruby, Python, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](https://github.com/lord/slate) and borrows from the awesome documentation over at [Stripe] (https://stripe.com/docs/api). Feel free to edit it and use it as a base for your own API's documentation.

# Versioning

We use versioning to roll out new API features and ensure our versions are backwards compatible. The current version is 2018-10-21 (0.0.1).

# Authentication

> To authorize, use this code:

```ruby
require 'vandelay'

api = Vandelay::APIClient.authorize!('ringringring')
```

```python
import vandelay

api = vandelay.authorize('ringringring')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: ringringring"
```

```javascript
const vandelay = require('vandelay');

let api = vandelay.authorize('ringringring');
```

> Make sure to replace `ringringring` with your API key.

Vandelay uses API keys to allow access to the API. Your API keys carry many privileges, so be sure to keep them secure! Do not share your secret API keys in publicly accessible areas such as GitHub, client-side code, and so forth. 

You can register a new Vandelay API key at our [developer portal](https://api.vandelay.com/developers).

All API requests must be made over HTTPS. Calls made over plain HTTP will fail. API requests without authentication will also fail.

Vandelay expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: ringringring`

<aside class="notice">
You must replace <code>ringringring</code> with your personal API key.
</aside>

# Idempotency

The API supports idempotency for safely retrying requests without accidentally performing the same operation twice. This is useful when an API call is disrupted in transit and you do not receive a response. For example, if a request fails due to a network connection error, you can retry the request without generating duplicates.

# Factories

## Get Factories

```ruby
require 'vandelay'

api = Vandelay::APIClient.authorize!('ringringring')
api.factories.get()
```

```python
import vandelay

api = vandelay.authorize('ringringring')
api.factories.get()
```

```shell
curl "https://api.vandelay.com/factories"
  -H "Authorization: ringringring"
```

```javascript
const vandelay = require('vandelay');

let api = vandelay.authorize('ringringring');
let factories = api.factories.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 2,
    "name": "Newark Latex Mfg.",
    "description": "East Coast facility for raw latex material 
    to be processed into final products for the medical industry.",
    "address": {
      "buildingName": "Newark East Coast Site",
      "streetLine1": "1838 Adam Clayton Powell Avenue",
      "streetLine2": "Apartment 7",
      "city": "New York",
      "stateProvince": "New York",
      "zipPostalCode":  10032,
      "country": "USA"
    }
   }
  ]
```

This endpoint retrieves all factories.

### HTTPS Request

`GET https://api.vandelay.com/factories`

<aside class="success">
Remember — to retrieve factories, you must first authenticate.
</aside>

## Get Factory Machines

```ruby
require 'vandelay'

api = Vandelay::APIClient.authorize!('ringringring')
api.factory.machines.get(2)
```

```python
import vandelay

api = vandelay.authorize('ringringring')
api.factory.machines.get(2)
```

```shell
curl "https://api.vandelay.com/factories/2/machines"
  -H "Authorization: ringringring"
```

```javascript
const vandelay = require('vandelay');

let api = vandelay.authorize('ringringring');
let machines = api.machines.get(2);
```

> The above command returns JSON structured like this:

```json
[
  {
    "factoryId": 2,
    "id": 12,
    "name": "Extruder AB-100".
    "description": "Extruder with 1,000fpm output capacity"
  }
  ]
```

This endpoint retrieves all machines for a given factory.

### HTTPS Request

`GET https://api.vandelay.com/factories/<factoryId>/machines`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
factoryId | true | id for the Vandelay factory housing the machine

<aside class="success">
Remember — to retrieve machines, you must first authenticate.
</aside>

# Warehouses

## Get Warehouses

```ruby
require 'vandelay'

api = Vandelay::APIClient.authorize!('ringringring')
api.warehouses.get()
```

```python
import vandelay

api = vandelay.authorize('ringringring')
api.warehouses.get()
```

```shell
curl "https://api.vandelay.com/warehouses"
  -H "Authorization: ringringring"
```

```javascript
const vandelay = require('vandelay');

let api = vandelay.authorize('ringringring');
let warehouses = api.warehouses.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 10, 
    "name": "Pier 10 Holdings",
    "description": "Key East Coast shipping/receiving location for 
     storing finished product, ready for distribution."
    "address": {
      "buildingName": "Pier 10 East Coast Site",
      "streetLine1": "1538 Saint Nicholas Avenue",
      "streetLine2": "Apartment 5",
      "city": "New York",
      "stateProvince": "New York",
      "zipPostalCode":  10033,
      "country": "USA"
      }
   }
  ]
```

This endpoint retrieves all warehouses.

### HTTPS Request

`GET https://api.vandelay.com/warehouses`

<aside class="success">
Remember — to retrieve warehouses, you must first authenticate.

</aside>

## Get Warehouse Items

```ruby
require 'vandelay'

api = Vandelay::APIClient.authorize!('ringringring')
api.warehouses.items.get(2)
```

```python
import vandelay

api = vandelay.authorize('ringringring')
api.warehouses.items.get(2)
```

```shell
curl "https://api.vandelay.com/warehouses/6/items"
  -H "Authorization: ringringring"
```

```javascript
const vandelay = require('vandelay');

let api = vandelay.authorize('ringringring');
let items = api.warehouses.items.get(2);
```

> The above command returns JSON structured like this:

```json
[
  {
    "warehouseId": 6,
    "id": 55,
    "SKU" "TG-AS-SEAL-B":
    "quantity": 2,
    "name": "Waterproof seal",
    "description": "For sealing specimens to preserve them"
    }
  ]
```

This endpoint retrieves all items in the inventory for a given warehouse.

### HTTPS Request

`GET https://api.vandelay.com/warehouses/<warehouseId>/items`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
warehouseId | true | id for the Vandelay warehouse containing the items

<aside class="success">
Remember — to retrieve warehouse items, you must first authenticate.
</aside>
