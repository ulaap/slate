---
title: API Reference

language_tabs:
  - php

toc_footers:
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

RESTful APIs have proven to be more efficient, manageable, scalable and provide high availability.  Many of the leading companies in the world provide RESTful API’s including: Google, Facebook, Amazon, eBay, Twitter and others.

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
<?php
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
?>
```
> The above code returns JSON structured like this:

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

<aside class="warning">
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


> The above code returns JSON structured like this:

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
"carrier_contact_uuid": "",
"load_cubes": ""
}
]
```

This endpoint retrieves all ladings.

### HTTP Request

`GET https://example.com/app/api/5/ladings_list/?key=<api_key>`

### HTTP Request With Query Parameters
`GET https://example.com/app/api/5/ladings_list/?key=<api_key>&pro_bill=<any_pro_bill_number>`
`GET https://example.com/app/api/5/ladings_list/?key=<api_key>&lading_status=<int>`

<aside class="notice">
You must replace <code>api_key</code> with your personal API key.
You must replace <code>any_pro_bill_number</code> with a pro bill number you want to query.
You must replace <code>int</code> with interger value of a lading status (see below).
</aside>

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
carrier_contact_uuid |  | If set to contact_uuid of a carrier, it will pass all the ladings with that carrier. 
pro_bill |  | If set to a pro bill number, it will pass the lading with that pro bill number.
lading_status |  | If set to a lading status integer value, it will pass all the ladings with that status.

### Lading Status Enum Int Value

Int | Enum 
--------- | -----------
1 | En Route Shipper
2 | Arrived Shipper
3 | Detained Shipper
4 | Loading Shipper
5 | Loaded Shipper
6 | En Route Consignee 
7 | Arrived Consignee
8 | Detained Consignee
9 | Unloading Consignee
10 | Delivered Consignee
11 | Delay Mechanical
12 | Delay Traffic
13 | Delay Accident
14 | Delay Weather
15 | Delay Inspection
16 | Delay Other
17 | Load Check
18 | Load Temperature Check
19 | Load Scale
20 | Load Damage
21 | Load Completed

### JSON Name, Type, and Value Description

Name | Data Type | Description
--------- | --------- | -----------
alternate_reference | text | An alternate reference alphanumeric for tracking tasks
broker_mc | text | Motor Carrier prefix registered for freight broker organization user 
brokered_date | text | Date haulage was arranged with carrier 
carrier_contact_uuid | uuid | The UUID for the carrier contact #create-a-contact 
carrier_mc | text | Motor Carrier prefix registered for transportation organization user 
carrier_tractor | text | Tractor identifier number used by carrier
carrier_trailer | text | Trailer identifier number used by carrier
consignee_contact_uuid | uuid | The UUID for the consignee contact #create-a-contact 
consignee_locality | text | The town, city, or community name of the consignee 
consignee_name | text | Name of consignee
consignee_region | text | The state or province of the consignee
damage_note | text | Description of the damage to the load being hauled 
damage_photo | text | Photo of load damaged during cartage
domain_uuid | uuid | UUID of the Doamin 
equipment_options | text | Carrier using additional equipment options
lading_number | text | Bill of lading reference number or alphanumeric
lading_status | int | Status of lading see Lading Status Enum Int Value table 
lading_status_updated | timestamp | Date and time the lading status was updated 
lading_uuid | uuid | UUID of lading 
load_cubes | text | Cubic foot measure of a load
load_details | text | Details or remarks regarding the content of the load for bill of lading requirement 
load_end | timestamp | The end or final delivery time designated for the given task or load
load_length | text | Length of load listed
load_pallets | text | Number of pallets comprising the load 
load_pieces | text | Number of pieces part of load
load_special_info | text | Special information note related to load haulage
load_start | timestamp | The start or pick-up time designated for the given task or load
load_value | text | Declared Value of load for bonding purposes or export 
load_weight | text | Weight of load listed
load_weight_actual | text | Actual weight of load when measured 
partial_or_full | text | Designates if load is a full trailer or less than a trailer capacity
pay_advance | text | Specifies if carrier was given an advance or had a deduction made against the "rate payment"
payment_reference | text | Payment reference number or identifier used by the factoring company
pro_bill | text | Carrier Pro Bill number or Load ID number
rate_confirmation | text | Rate confirmation identifier number used to validate haulage agreement 
rate_pay | text | Rate paid to carrier for haulage
seal_number | text | Customer customs or bonding seal to secure a load for transport
shipment_number | text | Shipper / Customer designated reference number or purchase order to track load
shipper_contact_uuid | uuid | The UUID for the shipper contact #create-a-contact 
shipper_locality | text | The town, city, or community name of the shipper
shipper_name | text | The name of the shipper
shipper_region | text | The state or province of the shipper
trip_number | text | Trip number used to consolidate information for accounting purposes
type_of_equipment | text | Type of trailer equipment required to haul load
user_uuid | uuid | UUID of user

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

> The above code returns JSON structured like this:

```json
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
"load_special_info": "Consignee notes: RECEIVING HOURS ARE FROM 7AM TO16:30PM",
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
"carrier_tractor": null,
"lading_status": "0",
"damage_photo": null,
"user_uuid": null,
"lading_tasks": [
        {
        "signature_uuid": null,
        "domain_uuid": "",
        "task_note": null,
        "good_type": null,
        "contact_uuid": "",
        "load_start": null,
        "lading_uuid": "",
        "date": null,
        "lading_task_uuid": "",
        "load_end": null,
        "scan_document_uuid": null,
        "task_type": "1",
        "scan_uuid": null
        },
        {
        "signature_uuid": null,
        "domain_uuid": "",
        "task_note": null,
        "good_type": null,
        "contact_uuid": "",
        "load_start": null,
        "lading_uuid": "",
        "date": null,
        "lading_task_uuid": "",
        "load_end": null,
        "scan_document_uuid": null,
        "task_type": "2",
        "scan_uuid": null
        },
        {
        "signature_uuid": null,
        "domain_uuid": "",
        "task_note": null,
        "good_type": null,
        "contact_uuid": "",
        "load_start": null,
        "lading_uuid": "",
        "date": null,
        "lading_task_uuid": "",
        "load_end": null,
        "scan_document_uuid": null,
        "task_type": "6",
        "scan_uuid": null
        }
                    ],
"type_of_equipment": null,
"rate_pay": null,
"load_weight": "516",
"lading_uuid": "",
"load_details": "PIECES-(3) MS701 SMOOTH #50175",
"rate_confirmation": null,
"partial_or_full": null,
"load_end": "2015-04-29 00:00:00",
"shipper_contact_uuid": "",
"carrier_contact_uuid": "",
"lading_logs": [

]
}

```

This endpoint retrieves a specific lading.

### HTTP Request

`GET https://example.com/app/api/5/ladings/<lading_uuid>/?key=<api_key>`

<aside class="warning">
You must replace <code>\<lading_uuid\></code> with the UUID of the desired lading.
</aside>

### URL Parameters

Parameter | Description
--------- | -----------
key | The API key

<aside class="notice">
See JSON value, types, and descriptions of <a href="http://ulaap.com:4567/#get-all-ladings">ladings</a>
</aside>

<aside class="notice">
See JSON value, types, and descriptions of [lading_tasks](#error-code-definitions)
</aside>


## Create a Lading

```php
<?php

// The data to send to the API
$postData = array(
'pay_advance' => $payAdvance,
'load_pieces' => $loadPieces,
'seal_number' => $sealNumber,
'equipment_options' => $equipmentOptions, 
'rated_miles' => $ratedMiles,
'load_pallets' => $loadPallets,
'carrier_mc' => $carrierMc,
'load_length' => $loadLength,
'carrier_trailer' => $carrierTrailer, 
'shipper_locality' => $shipperLocality, 
'alternate_reference' => $alternateReference, 
'brokered_date' => $brokeredDate, 
'load_special_info' => $loadspecialInfo,
'damage_note' => $damageNote,
'trip_number' => $tripNumber,
'shipment_number' => $shipmentNumber,
'load_value' => $loadValue,
'lading_number' => $ladingNumber,
'load_weight_actual' => $loadWeightActual,
'payment_reference' => $paymentReference,
'broker_mc' => $brokerMc,
'load_start' => $loadStart,
'pro_bill' => $proBill,
'carrier_tractor' => $carrierTractor,
'lading_status' => $ladingStatus,
'damage_photo' => $damagePhoto,
'type_of_equipment' => $typeOfEquipment,
'rate_pay' => $ratePay,
'load_weight' => $loadWeight,
'load_details' => $loadDetails,
'rate_confirmation' => $rateConfirmation,
'carrier_contact_uuid' => $carrierContactUuid,
'partial_or_full' => $partialOrFull,
'load_end' => $loadEnd 
);

// Setup cURL
$ch = curl_init('https://example/app/api/5/ladings/?key={$api_key}');
curl_setopt_array($ch, array(
CURLOPT_POST => TRUE,
CURLOPT_SSL_VERIFYPEER => false,
CURLOPT_SSL_VERIFYHOST => false,
CURLOPT_RETURNTRANSFER => TRUE,
CURLOPT_HTTPHEADER => array(
'Content-Type: application/json'
),
CURLOPT_POSTFIELDS => json_encode($postData)
));

// Send the request
$response = curl_exec($ch);

// Check for errors
if($response === FALSE){
die(curl_error($ch));
}

// Decode the response
$responseData = json_decode($response, TRUE);

//Get the lading UUID
$ladingUuid = $responseData['details']['0']['uuid'];
?>
```
> $ladingUuid will be used when creating a [lading task.](#create-a-lading-task)

> The above code returns JSON structured like this:

```json
{
"code": "200", 
"details": [
{
"code": "200",
"uuid": "1cf8c03c-3f1b-4ee5-ba1f-360b99519ef1",
"name": "ladings",
"sql": "INSERT INTO v_ladings (lading_uuid, domain_uuid, pay_advance, load_pieces, seal_number, equipment_options, rated_miles,
load_pallets, carrier_mc, load_length, carrier_trailer, shipper_locality, alternate_reference, brokered_date, load_special_info, damage_note, trip_number, shipment_number, load_value, lading_number, load_weight_actual, payment_reference, broker_mc, load_start, pro_bill, carrier_tractor, lading_status, damage_photo, type_of_equipment, rate_pay, load_weight, load_details, rate_confirmation, partial_or_full, load_end) VALUES ('1cf8c03c-3f1b-4ee5-ba1f-360b99519ef1', '', '', '20', null, '', '', '', '', '', '', '', '', 'January 24, 2014', '', '', '174744', '915439', '', '', '', '', '', 'January 24, 2014', '915439', '', '', '13', '', '', '', '294', '', '', '', 'January 24, 2014');",
"message": "OK" }
],
"message": "OK" }

```

This endpoint creates a lading.

### HTTP Request

`POST https://example.com/app/api/5/ladings/?key=<api_key>`

### JSON Request Body

`{
"pay_advance": "",
"load_pieces": "20",
"seal_number": null,
"equipment_options": "", 
"rated_miles": "",
"load_pallets": "",
"carrier_mc": "",
"load_length": "",
"carrier_trailer": "", 
"shipper_locality": "", 
"alternate_reference": "", 
"brokered_date": "January 24, 2014", 
"load_special_info": "",
"damage_note": "",
"trip_number": "174744",
"shipment_number": "915439",
"load_value": "",
"lading_number": "",
"load_weight_actual": "",
"payment_reference": "",
"broker_mc": "",
"load_start": "January 24, 2014",
"pro_bill": "915439",
"carrier_tractor": "",
"lading_status": "13",
"damage_photo": "",
"type_of_equipment": "",
"rate_pay": "",
"load_weight": "294",
"load_details": "",
"rate_confirmation": “",
"carrier_contact_uuid": “",
"partial_or_full": "",
"load_end": "January 24, 2014" 
}`

### URL Parameters

Parameter | Description
--------- | -----------
key | The API key

# Contacts

## Get All Contacts

```php
<?php
// Setup cURL
$ch = curl_init();
curl_setopt_array($ch, array(
CURLOPT_URL => "https://example.com/app/api/5/contacts?key={$api_key}",
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


> The above code returns JSON structured like this:

```json
[
{
"legal_name": null,
"contact_email": null,
"contact_name_suffix": null,
"us_dot_no": null,
"active": null,
"domain_uuid": "",
"contact_nickname": null,
"contact_role": null,
"contact_note": null,
"contact_time_zone": null,
"contact_uuid": "",
"contact_category": null,
"contact_name_prefix": null,
"contact_type": "1",
"contact_organization": "Example Organization",
"contact_url": null,
"contact_parent_uuid": null,
"contact_name_given": null,
"last_mod_user": null,
"contact_title": null,
"created_by": null,
"last_mod_date": null,
"contact_name_middle": null,
"created": null,
"contact_name_family": null
},
{
"legal_name": null,
"contact_email": null,
"contact_name_suffix": null,
"us_dot_no": null,
"active": null,
"domain_uuid": "",
"contact_nickname": null,
"contact_role": null,
"contact_note": null,
"contact_time_zone": null,
"contact_uuid": "",
"contact_category": null,
"contact_name_prefix": null,
"contact_type": "2",
"contact_organization": "Example Organization 2",
"contact_url": null,
"contact_parent_uuid": null,
"contact_name_given": null,
"last_mod_user": null,
"contact_title": null,
"created_by": null,
"last_mod_date": null,
"contact_name_middle": null,
"created": null,
"contact_name_family": null
}
]
```

This endpoint retrieves all contacts.

### HTTP Request

`GET https://example.com/app/api/5/contacts?key=<api_key>`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
contact_organization | null | If set to name of a contact organization, it will pass the contact with that organization name. 
active | null | If set to true, it will pass all active contacts.
contact_type |  | If set to a contact type integer value, it will pass all the contacts with that task type.
key |  | The API Key

<aside class="notice">
You can see the integer values for lading statuses by looking under `int enum values`.
</aside>

## Get a Specific Contact

```php
<?php
// Setup cURL
$ch = curl_init();
curl_setopt_array($ch, array(
CURLOPT_URL => "https://example.com/app/api/5/contacts/{$contact_uuid}?key={$api_key}",
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

> The above code returns JSON structured like this:

```json
{
"last_mod_date": null,
"contact_category": null,
"legal_name": null,
"contact_relations": [

],
"contact_notes": [

],
"contact_name_prefix": null,
"contact_title": null,
"contact_emails": [

],
"contact_settings": [

],
"created": null,
"contact_uuid": "",
"contact_time_zone": null,
"contact_name_middle": null,
"us_dot_no": null,
"contact_addresses": [
{
"address_label": null,
"domain_uuid": "",
"address_region": "PQ",
"address_postal_code": "H4B 1R2",
"contact_uuid": "",
"address_description": null,
"address_type": null,
"address_locality": "MONTREAL",
"address_street": "",
"address_country": "CANADA",
"contact_address_uuid": "",
"address_extended": null,
"address_latitude": null,
"address_longitude": null,
"address_primary": "0",
"address_community": null
}
],
"contact_note": null,
"contact_nickname": null,
"contact_role": null,
"created_by": null,
"domain_uuid": "",
"last_mod_user": null,
"contact_name_family": null,
"contact_urls": [

],
"active": null,
"contact_type": "2",
"contact_name_suffix": null,
"contact_email": null,
"contact_url": null,
"contact_parent_uuid": null,
"contact_groups": [

],
"contact_organization": "Example Organization 2",
"contact_name_given": null,
"contact_phones": [
{
"phone_type_video": null,
"domain_uuid": "",
"contact_phone_uuid": "",
"phone_type": null,
"phone_label": null,
"contact_uuid": "",
"phone_description": null,
"phone_extension": "",
"phone_type_voice": null,
"phone_number": "",
"phone_type_text": null,
"phone_type_fax": null,
"phone_primary": "0"
}
]
}

```

This endpoint retrieves a specific contact.

### HTTP Request

`GET https://example.com/app/api/5/contacts/<contact_uuid>/?key=<api_key>`

### URL Parameters

Parameter | Description
--------- | -----------
contact_uuid | The UUID of the contact to retrieve.
key | The API key.

## Create a Contact

```php
<?php

// The data to send to the API
$postData = array(
'contact_email' => $contactEmail,
'contact_nickname' => $contactNickname,
'contact_role' => $contactRole,
'contact_note' => $contactNote, 
'contact_time_zone' => $contactTimeZone,
'contact_category' => $contactCategory,
'contact_type' => $contactType,
'contact_organization' => $contactOrganization,
'contact_url' => $contactUrl, 
'contact_name_given' => $contactNameGiven, 
'contact_title' => $contactTitle, 
'created_by' => $createdBy, 
'created' => $created,
'contact_name_family' => $contactNameFamily,
'contact_addresses' => array(
    'address_region' => $addressRegion,
    'address_postal_code' => $addressPostalCode,
    'address_description' => $addressDescription,
    'address_type' => $addressType,
    'address_locality' => $addressLocality,
    'address_street' => $addressStreet,
    'address_country' => $addressCountry,
    'address_extended' => $addressExtended,
    'address_latitude' => $addressLatitude,
    'address_longitude' => $addressLongitude),
'contact_phones' => array(
    'phone_type' => $phoneType,
    'phone_description' => $phoneDescription,
    'phone_extension' => $phoneExtension,
    'phone_number' => $phoneNumber)
    
);

// Setup cURL
$ch = curl_init('https://example/app/api/5/contacts/?key={$api_key}');
curl_setopt_array($ch, array(
CURLOPT_POST => TRUE,
CURLOPT_SSL_VERIFYPEER => false,
CURLOPT_SSL_VERIFYHOST => false,
CURLOPT_RETURNTRANSFER => TRUE,
CURLOPT_HTTPHEADER => array(
'Content-Type: application/json'
),
CURLOPT_POSTFIELDS => json_encode($postData)
));

// Send the request
$response = curl_exec($ch);

// Check for errors
if($response === FALSE){
die(curl_error($ch));
}

// Decode the response
$responseData = json_decode($response, TRUE);

//Get the contact UUID
$contactUuid = $responseData['details']['0']['uuid'];
?>
```
> $contactUuid will be used when creating a [lading task.](#create-a-lading-task)

> The above code returns JSON structured like this:

```json
{
"code": "200",
"details": [
{
"code": "200",
"uuid": "61748b85-1f82-4dda-bdcf-1edc454cf9fe",
"name": "contacts",
"sql": "INSERT INTO v_contacts (domain_uuid, contact_uuid, contact_email, contact_nickname, contact_role, contact_note, contact_time_zone, contact_category, contact_type, contact_organization, contact_url, contact_name_given, contact_title, created_by, created, contact_name_family) VALUES ('12fcbe40-c1f1-4e36-85bc-6f0fa0433bc2', '61748b85-1f82-4dda-bdcf-1edc454cf9fe', '', '', '', '', '', '', '', '', '', '', '', '', '', '');",
"message": "OK"
},
{
"code": "200",
"uuid": "0816e85c-59e5-4068-ba95-97be48a7f052",
"name": "contact_phones",
"sql": "INSERT INTO v_contact_phones (domain_uuid, contact_uuid, contact_phone_uuid, phone_type, phone_description, phone_extension, phone_number) VALUES ('12fcbe40-c1f1-4e36-85bc-6f0fa0433bc2', '61748b85-1f82-4dda-bdcf-1edc454cf9fe', '0816e85c-59e5-4068-ba95-97be48a7f052', '', '', '', '');",
"message": "OK"
}
],
"message": "OK"
}


```

This endpoint creates a contact.

### HTTP Request

`POST https://example.com/app/api/5/contacts/?key=<api_key>`

### JSON Request Body

`{
"contact_email": "",
"contact_nickname": "",
"contact_role": "",
"contact_note": "",
"contact_time_zone": "",
"contact_category": "",
"contact_addresses":` [`{
    "address_region": "", 
    "address_postal_code": "",
    "address_description": "",
    "address_type": "",
    "address_locality": "",
    "address_street": "",
    "address_country": "",
    "address_extended": "",
    "address_latitude": "",
    "address_longitude": ""
    }` ]`,
"contact_type": "",
"contact_organization": "",
"contact_phones":` [`{
    "phone_type": "",
    "phone_description": "",
    "phone_extension": "",
    "phone_number": ""
    }` ]`,
"contact_url": "",
"contact_name_given": "",
"contact_title": "",
"created_by": "",
"created": "",
"contact_name_family": ""
}`

### URL Parameters

Parameter | Description
--------- | -----------
key | The API key

#Lading Tasks

## Create a Lading Task

```php
<?php

// The data to send to the API
$postData = array(
'contact_uuid' => $contactUuid,
'lading_uuid' => $ladingUuid,
'good_type' => $goodType,
'load_start' => $loadStart, 
'date' => $date,
'load_end' => $loadEnd,
'task_type' => $taskType);

// Setup cURL
$ch = curl_init('https://example/app/api/5/lading_tasks/?key={$api_key}');
curl_setopt_array($ch, array(
CURLOPT_POST => TRUE,
CURLOPT_SSL_VERIFYPEER => false,
CURLOPT_SSL_VERIFYHOST => false,
CURLOPT_RETURNTRANSFER => TRUE,
CURLOPT_HTTPHEADER => array(
'Content-Type: application/json'
),
CURLOPT_POSTFIELDS => json_encode($postData)
));

// Send the request
$response = curl_exec($ch);

// Check for errors
if($response === FALSE){
die(curl_error($ch));
}

// Decode the response
$responseData = json_decode($response, TRUE);

//Get the lading_task_uuid UUID
$ladingTaskUuid = $responseData['details']['0']['uuid'];
?>
```

> The above code returns JSON structured like this:

```json
{
"code": "200",
"details": [
{
"code": "200",
"uuid": "1e1e3d9b-b760-4802-a604-b1d613d9b8ef",
"name": "lading_tasks",
"sql": "INSERT INTO v_lading_tasks (domain_uuid, lading_task_uuid, contact_uuid, lading_uuid, good_type, load_start, date, load_end, task_type) VALUES ('', '1e1e3d9b-b760-4802-a604-b1d613d9b8ef', null, null, null, '2014-04-04 12:00:00-07', '2014-01-24 00:00:00', '2014-04-04 20:00:00-07', '1');",
"message": "OK"
}
],
"message": "OK"
}

```

This endpoint creates a lading task.

### HTTP Request

`POST https://example.com/app/api/5/lading_tasks/key=<api_key>`

### JSON Request Body

`{
"contact_uuid": null,
"lading_uuid": null,
"good_type": "",
"load_start": "2014-04-04 12:00:00-07",
"date": "2014-01-24 00:00:00",
"load_end": "2014-04-04 20:00:00-07",
"task_type": "1"
}`

### URL Parameters

Parameter | Description
--------- | -----------
key | The API key

### JSON Name and Value Description

Name | Description
--------- | -----------
contact_uuid | The UUID for the [contact.](#create-a-contact)
lading_uuid | The UUID for the [lading.](#create-a-lading)
good_type | Type of goods.
load_start | Date and time the load starts. 
date | Date and time lading task was created.
load_end | Date and time the load ends. 
task_type | Type of task.

### Task Type Enum Int Value

Int | Enum 
--------- | -----------
1 | Shipper
2 | Consignee
3 | Consignee stop 2
4 | Consignee stop 3 
5 | Dispatch
6 | Carrier 
7 | Driver
8 | Payment Factor


