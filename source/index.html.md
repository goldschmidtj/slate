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

This example API documentation page was created with [Slate](https://github.com/lord/slate). Feel free to edit it and use it as a base for your own API's documentation.

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

Vandelay uses API keys to allow access to the API. You can register a new Vandelay API key at our [developer portal](https://api.vandelay.com/developers).

Vandelay expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: ringringring`

<aside class="notice">
You must replace <code>ringringring</code> with your personal API key.
</aside>

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

## Get Machines

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

`GET https://api.vandelay.com/factories/<ID>/machines`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
factoryId | true | id for the Vandelay factory housing the machine

<aside class="success">
Remember — to retrieve machines, you must first authenticate.
</aside>

# Kittens

## Get All Kittens

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "https://example.com/api/kittens"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTPS Request

`GET https://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "https://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTPS Request

`GET https://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "https://example.com/api/kittens/2"
  -X DELETE
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTPS Request

`DELETE https://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

