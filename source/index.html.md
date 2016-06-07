---
title: API Reference

language_tabs:
  - php

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

## Purpose

With an easy to use smartphone app, a web portal and a fully interoperable Application Program Interface (API), Ulaap facilitates dispatching a service provider (driver, technician, mobile service worker, etc.) to complete a series of tasks related to a service.  The first release of Ulaap is focused at truckload and less-than-truckload transportation services but future iterations plan to provide solutions for field service technicians, home healthcare providers as provide solutions for field service technicians, home healthcare providers as well as other mobile workforces.

Ulaap on iOS and Android enables the end-user to update statuses and provide other information related to task performance.  Common workflow processes such as signature verification, barcode, QR code and document scanning functionality are exchanged in real-time with other validation services.

Our Representational State Transfer (RESTful) API provides responses in JSON format for easy integration to legacy operating systems.   For those that don’t have back office systems, our portal allows end-users to take full advantage of Ulaap functionality with no upfront investment.

Subsequent releases of Ulaap’s transportation app will include “onboarding” services such as: carrier confirmation forms, rate confirmations, WSIB/W9 data, insurance (i.e. auto, GL, cargo limits and expiry dates) as well as other critical verification and compliance information.

## Intergration

RESTful APIs have proven to be more efficient, manageable, scalable and provide high availability.  Many of the leading companies in the world provide RESTful API’s including: Google, Facebook, Amazon, EBay, Twitter and others.

### Our Ulaap REST API offers:
* Enhanced security through a unique token;
* Quicker, lighter transaction processes that eliminate parsing or handling unnecessary headers;
* Flexible call architecture that do not sacrifice data integrity;
* Interoperability with independently developed, owned and/or purchased dispatch (TMS) systems, inventory systems, accounting solutions and so on.

### Usage guidelines behind the API support:
* Ancillary services and requirements affecting payment for cartage (i.e. automated validation to third-parties payees);
* Information related to insurance and/or bonding processes;
* Permit related services;
* Service value-adds beyond the functionality of what legacy EDI applications can provide (i.e. real-time signature capture, efficient document scanning);
* Increasing accountability and responsiveness in transactions between parties without reliance on email, fax, phone or other.

## Customized or Purpose Built Releases
We build development cases for enhancing functionality or implementing new service modules based on fairly practical processes.  Together with industry advisors, partners and customers we assess and determine the feasibility of a product, service or feature to satisfy a specific demand or fill a service void.  By interviewing, listening, sharing ideas, bridging concepts and understanding the requirements of end-users, we fuse together a wide knowledge base to add to functionality.  Our continual consultations enable us to engineer solutions in our app and API that compliment each and every task or transaction that is executed as part of our end-user’s business processes.

Ulaap tools strengthen real-time accountability and make your company more attractive to current and new clients.

Designed as a unified platform, Ulaap keeps your development and deployment resources in check.  Let our tools help you do the business that you need to do.

# Authentication

> To authorize, use this code:

```php
// Setup cURL
$ch = curl_init();
curl_setopt_array($ch, array(
CURLOPT_URL => "https://example.com/app/api/5/api_key?username={$username}&password={$password}",
CURLOPT_SSL_VERIFYPEER => false,
CURLOPT_SSL_VERIFYHOST => false,
CURLOPT_RETURNTRANSFER => TRUE,
CURLOPT_HTTPHEADER => array(
'Content-Type: application/json'
),

));

// Send the request
$response = curl_exec($ch);

// Check for errors
if($response === FALSE){
die(curl_error($ch));
}

// Decode the response
$responseData = json_decode($response, TRUE);
```
> The above command returns JSON structured like this:

```json
[
"result": {
"domain_uuid": "",
"carrier_contact_uuid": "",
"user_uuid": "",
"api_key": ""
}
]
```

> Make sure to replace `$username` and `$passord` with your username and password.

Ulaap uses API keys to allow access to the API. You can fetch your API key by passing your username and password in a GET request.

Ulaap expects for the API key to be included in all API requests to the server in a URL parameter that looks like the following:

`?key=api_key`

<aside class="notice">
You must replace <code>api_key</code> with your personal API key.
</aside>

# Ladings

## Get All Ladings

```php
<?php
// Setup cURL
$ch = curl_init();
curl_setopt_array($ch, array(
CURLOPT_URL => "https://example.com/app/api/5/ladings_list?key={$api_key}",
CURLOPT_SSL_VERIFYPEER => false,
CURLOPT_SSL_VERIFYHOST => false,
CURLOPT_RETURNTRANSFER => TRUE,
CURLOPT_HTTPHEADER => array(
'Content-Type: application/json'
),

));

// Send the request
$response = curl_exec($ch);

// Check for errors
if($response === FALSE){
die(curl_error($ch));
}

// Decode the response
$responseData = json_decode($response, TRUE);
?>
```


> The above command returns JSON structured like this:

```json
[
{
"shipper_region": null,
"consignee_name": null,
"pay_advance": null,
"lading_status_updated": null,
"load_pieces": "3",
"seal_number": null,
"equipment_options": null,
"rated_miles": null,
"consignee_locality": null,
"consignee_region": null,
"load_pallets": null,
"carrier_mc": null,
"domain_uuid": "",
"load_length": null,
"carrier_trailer": null,
"shipper_locality": null,
"alternate_reference": "202740-01",
"brokered_date": null,
"load_special_info": "",
"damage_note": null,
"trip_number": "",
"shipper_name": null,
"consignee_contact_uuid": "",
"shipment_number": null,
"load_value": null,
"lading_number": "",
"load_weight_actual": "516",
"payment_reference": null,
"broker_mc": null,
"load_start": "2015-04-23 00:00:00",
"pro_bill": "4288109750",
"truckstop_post": null,
"carrier_tractor": null,
"lading_status": "0",
"damage_photo": null,
"user_uuid": null,
"type_of_equipment": null,
"rate_pay": null,
"load_weight": "516",
"lading_uuid": "",
"load_details": "PIECES-(3) MS701 SMOOTH #50175",
"rate_confirmation": null,
"partial_or_full": null,
"load_end": "2015-04-29 00:00:00",
"shipper_contact_uuid": "",
"carrier_contact_uuid": ""
},
{
"shipper_region": null,
"consignee_name": null,
"pay_advance": null,
"lading_status_updated": null,
"load_pieces": "15",
"seal_number": null,
"equipment_options": null,
"rated_miles": null,
"consignee_locality": null,
"consignee_region": null,
"load_pallets": null,
"carrier_mc": null,
"domain_uuid": "",
"load_length": null,
"carrier_trailer": null,
"shipper_locality": null,
"alternate_reference": "203252-01",
"brokered_date": null,
"load_special_info": "",
"damage_note": null,
"trip_number": "",
"shipper_name": null,
"consignee_contact_uuid": "",
"shipment_number": null,
"load_value": null,
"lading_number": "212689",
"load_weight_actual": "83",
"payment_reference": null,
"broker_mc": null,
"load_start": "2015-05-08 00:00:00",
"pro_bill": "1013994898",
"truckstop_post": null,
"carrier_tractor": null,
"lading_status": "21",
"damage_photo": null,
"user_uuid": null,
"type_of_equipment": null,
"rate_pay": null,
"load_weight": "83",
"lading_uuid": "",
"load_details": "PIECES",
"rate_confirmation": null,
"partial_or_full": null,
"load_end": "2015-05-14 00:00:00",
"shipper_contact_uuid": "",
"carrier_contact_uuid": ""
}
]
```

This endpoint retrieves all ladings.

### HTTP Request

`GET https://example.com/app/api/5/ladings_list`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
carrier_contact_uuid |  | If set to contact_uuid of a carrier, it will pass all the ladings with that carrier. 
pro_bill |  | If set to a pro bill number, it will pass the lading with that pro bill number.
lading_status |  | If set to a lading status integer value, it will pass all the ladings with that status.

<aside class="notice">
You can see the integer values for lading statuses by looking under `int enum values`.
</aside>

## Get a Specific Lading

```php
<?php
// Setup cURL
$ch = curl_init();
curl_setopt_array($ch, array(
CURLOPT_URL => "https://example.com/app/api/5/ladings/{$lading_uuid}?key={$api_key}",
CURLOPT_SSL_VERIFYPEER => false,
CURLOPT_SSL_VERIFYHOST => false,
CURLOPT_RETURNTRANSFER => TRUE,
CURLOPT_HTTPHEADER => array(
'Content-Type: application/json'
),

));

// Send the request
$response = curl_exec($ch);

// Check for errors
if($response === FALSE){
die(curl_error($ch));
}

// Decode the response
$responseData = json_decode($response, TRUE);
?>
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

This endpoint retrieves a specific lading.

### HTTP Request

`GET https://example.com/app/api/5/ladings/{lading_uuid}/key={api_key}`

### URL Parameters

Parameter | Description
--------- | -----------
lading_uuid | The UUID of the lading to retrieve
key | The API key

