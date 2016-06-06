---
title: API Reference

language_tabs:
  - shell
  - ruby
  - python

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

## Purpose

With an easy to use smartphone app, a web portal and a fully interoperable Application Program Interface (API), Ulaap facilitates dispatching a service provider (driver, technician, mobile service worker, etc.) to complete a series of tasks related to a service.  The first release of Ulaap is focused at truckload and less-than-truckload transportation services but future iterations plan to provide solutions for field service technicians, home healthcare providers as well as other mobile workforces.  
Ulaap on iOS and Android enables the end-user to update statuses and provide other information related to task performance.  Common workflow processes such as signature verification, barcode, QR code and document scanning functionality are exchanged in real-time with other validation services.  
Our Representational State Transfer (RESTful) API provides responses in JSON format for easy integration to legacy operating systems.   For those that don’t have back office systems, our portal allows end-users to take full advantage of Ulaap functionality with no upfront investment.  
Subsequent releases of Ulaap’s transportation app will include “onboarding” services such as: carrier confirmation forms, rate confirmations, WSIB/W9 data, insurance (i.e. auto, GL, cargo limits and expiry dates) as well as other critical verification and compliance information.


## Integration

RESTful APIs have proven to be more efficient, manageable, scalable and provide high availability.  Many of the leading companies in the world provide RESTful API’s including: Google, Facebook, Amazon, EBay, Twitter and others. 
Our Ulaap REST API offers: 
* Enhanced security through a unique token;
* Quicker, lighter transaction processes that eliminate parsing or handling unnecessary headers;
* Flexible call architecture that do not sacrifice data integrity;
* Interoperability with independently developed, owned and/or purchased dispatch (TMS) systems, inventory systems, accounting solutions and so on.  

Usage guidelines behind the API support:
* Ancillary services and requirements affecting payment for cartage (i.e. automated validation to third-parties payees);
* Information related to insurance and/or bonding processes;
* Permit related services;
* Service value-adds beyond the functionality of what legacy EDI

# Authentication

> To authorize, use this code:

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: meowmeowmeow"
```

> Make sure to replace `meowmeowmeow` with your API key.

Kittn uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](http://example.com/developers).

Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
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
curl "http://example.com/api/kittens"
  -H "Authorization: meowmeowmeow"
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

### HTTP Request

`GET http://example.com/api/kittens`

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
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
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

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

