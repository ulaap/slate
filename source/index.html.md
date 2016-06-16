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

`?key=<api_key>`

<aside class="warning">
You must replace <code>&lt;api_key&gt;</code> with your personal API key.
</aside>

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

### URL Parameters

Parameter | Description
--------- | -----------
key | The API key

### HTTP Request With Query Parameters
`GET https://example.com/app/api/5/contacts/?key=<api_key>&contact_organization=<any_contact_organization_name>`

`GET https://example.com/app/api/5/contacts/?key=<api_key>&active=<boolean>`

`GET https://example.com/app/api/5/contacts/?key=<api_key>&contact_type=<int_for_contact_type>`

<aside class="notice">
You must replace <code>&lt;api_key&gt;</code> with your personal API key.<p>
You must replace <code>&lt;any_contact_organization_name&gt;</code> with a contact organization name you want to query.<p>
You must replace <code>&lt;int_for_contact_type&gt;</code> with interger value of a contact type (see below).
</aside>

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
contact_organization | null | If set to name of a contact organization, it will pass the contact with that organization name. 
active | null | If set to true, it will pass all active contacts.
contact_type | null | If set to a contact type integer value, it will pass all the contacts with that task type.

### Contact Type Enum Int Value

Int | Enum 
--------- | -----------
0 | Default
1 | Manufacturer
2 | Service Provider
3 | Contractor
4 | Shipper 
5 | Receiver Consignee
6 | Carrier 
7 | Payment Processor
8 | Vendor
9 | Reseller
10 | Distributor
11 | Agent
12 | Friend
13 | Family
14 | Volunteer
15 | Company Division
16 | Driver
17 | APP Client
18 | Logistics Broker
19 | Customs Broker
20 | Customer Bill To

### JSON Name, Type, and Value Description

Name | Data Type | Description
--------- | --------- | -----------
active | boolean | Determines if the contact is active
contact_category | text | A field designated for future use and particular to phone system integration
contact_email | text | Form of a valid email address
contact_name_family | text | The family or last name of the contact
contact_name_given | text | The given or first name of the contact 
contact_name_middle | text | 
contact_name_prefix | text | 
contact_name_suffix | text |  
contact_nickname | text | A text field that can be used as a well known reference for the contact that is not a proper name
contact_note | text | An open text field used to add a notation particular to the contact 
contact_organization | text | Proper name or business name used to identify the organization that the contact works for or is a part of
contact_parent_uuid | uuid | UUID of the contact's parent
contact_role | text | A designated "role" of a contact which is documented below
contact_time_zone | text | A "timezone" of a contact which is documented below
contact_title | text | A business title associated with the contact's position in the organization
contact_type | text | Designation given to the contact for grouping, sorting or filtering contacts (see above for int) 
contact_url | text | The website of the Organization that the contact is associated to
contact_uuid | uuid | UUID of the contact
created | text | A timestamp of when the contact record was created 
created_by | text | The capture of the API user credentials that were used to create the contact record 
domain_uuid | uuid | UUID of the domain
last_mod_date | text | 
last_mod_user | text |  
legal_name | text | 
us_dot_no | text | 


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
You must replace <code>api_key</code> with your personal API key.<p>
You must replace <code>any_pro_bill_number</code> with a pro bill number you want to query.<p>
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
"load_pieces": null,
"seal_number": null,
"equipment_options": null,
"rated_miles": null,
"consignee_locality": null,
"consignee_region": null,
"load_pallets": null,
"carrier_mc": null,
"domain_uuid": null,
"load_length": null,
"carrier_trailer": null,
"shipper_locality": null,
"alternate_reference": null,
"brokered_date": null,
"load_special_info": null,
"damage_note": null,
"trip_number": null,
"shipper_name": null,
"consignee_contact_uuid": null,
"shipment_number": null,
"load_value": null,
"lading_number": null,
"load_weight_actual": null,
"payment_reference": null,
"broker_mc": null,
"load_start": null,
"pro_bill": null,
"carrier_tractor": null,
"lading_status": null,
"damage_photo": null,
"user_uuid": null,
"lading_tasks": [
        {
        "signature_uuid": null,
        "domain_uuid": null,
        "task_note": null,
        "good_type": null,
        "contact_uuid": null,
        "load_start": null,
        "lading_uuid": null,
        "date": null,
        "lading_task_uuid": null,
        "load_end": null,
        "scan_document_uuid": null,
        "task_type": null,
        "scan_uuid": null
        },
        {
        "signature_uuid": null,
        "domain_uuid": null,
        "task_note": null,
        "good_type": null,
        "contact_uuid": null,
        "load_start": null,
        "lading_uuid": null,
        "date": null,
        "lading_task_uuid": null,
        "load_end": null,
        "scan_document_uuid": null,
        "task_type": null,
        "scan_uuid": null
        },
        {
        "signature_uuid": null,
        "domain_uuid": null,
        "task_note": null,
        "good_type": null,
        "contact_uuid": null,
        "load_start": null,
        "lading_uuid": null,
        "date": null,
        "lading_task_uuid": null,
        "load_end": null,
        "scan_document_uuid": null,
        "task_type": null,
        "scan_uuid": null
        }
                    ],
"type_of_equipment": null,
"rate_pay": null,
"load_weight": null,
"lading_uuid": null,
"load_details": null,
"rate_confirmation": null,
"partial_or_full": null,
"load_end": null,
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
You must replace <code>&lt;lading_uuid&gt;</code> with the UUID of the desired lading.
</aside>

### URL Parameters

Parameter | Description
--------- | -----------
key | The API key

### JSON Name, Type, and Value Description for Lading Tasks

Name | Data Type | Description
--------- | ----------- | -----------
contact_uuid | uuid | The UUID for the [contact](#create-a-contact)
lading_uuid | uuid | The UUID for the [lading](#create-a-lading)
good_type | text | Type of goods
load_start | timestamp | Date and time the load starts 
date | timestamp | Date and time lading task was created
load_end | timestamp | Date and time the load ends 
task_type | text | Type of task (see below for int value)

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

<aside class="notice">
See JSON value, types, and descriptions of <a href="http://ulaap.com:4567/#get-all-ladings">ladings</a>
</aside>

## Create a Lading

```php
<?php

// The data to send to the API
$postData = array(
'pro_bill' => NULL,
'trip_number' => NULL,
'partial_or_full' => NULL,
'shipment_number' => NULL,
'load_details' => NULL,
'load_special_info' => NULL,
'load_weight' => NULL,
'load_weight_actual' => NULL,
'load_length' => NULL,
'load_pieces' => NULL,
'load_pallets' => NULL,
'load_value' => NULL,
'damage_photo' => NULL,
'damage_note' => NULL,
'broker_mc' => NULL,
'carrier_mc' => NULL,
'carrier_tractor' => NULL,
'carrier_trailer' => NULL,
'type_of_equipment' => NULL,
'equipment_options' => NULL,
'rate_confirmation' => NULL,
'rate_pay' => NULL,
'pay_advance' => NULL,
'brokered_date' => NULL,
'rated_miles' => NULL,
'payment_reference' => NULL,
'lading_number' => NULL,
'alternate_reference' => NULL,
'seal_number' => NULL,
'load_start' => NULL,
'load_end' => NULL,
'lading_status' => NULL
'shipper_contact_uuid' => NULL,
'consignee_contact_uuid' => NULL,
'user_uuid' => NULL,
'lading_status_updated' => NULL,
'carrier_contact_uuid' => NULL,
'load_cubes' => NULL,
'lading_tasks' => 
array (
0 => 
array(
'contact_uuid' => NULL,
'signature_uuid' => NULL,
'scan_uuid' => NULL,
'date' => NULL,
'task_type' => NULL,
'good_type' => NULL,
'load_start' => NULL,
'load_end' => NULL,
'scan_document_uuid' => NULL,
'task_note' => NULL,
),
1 => 
array(
'contact_uuid' => NULL,
'signature_uuid' => NULL,
'scan_uuid' => NULL,
'date' => NULL,
'task_type' => NULL,
'good_type' => NULL,
'load_start' => NULL,
'load_end' => NULL,
'scan_document_uuid' => NULL,
'task_note' => NULL,
),
2 => 
array(
'contact_uuid' => NULL,
'signature_uuid' => NULL,
'scan_uuid' => NULL,
'date' => NULL,
'task_type' => NULL,
'good_type' => NULL,
'load_start' => NULL,
'load_end' => NULL,
'scan_document_uuid' => NULL,
'task_note' => NULL,
),
),
'lading_logs' => 
array (
),
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
> The above code returns JSON structured like this:

```json
{
"code": "200",
"details": [
{
"code": "200",
"uuid": "5948128a-3cc4-41a8-bf73-47f6ade8b849",
"name": "ladings",
"sql": "INSERT INTO v_ladings (lading_uuid, pro_bill, trip_number, partial_or_full, shipment_number, load_details, load_special_info, load_weight, load_weight_actual, load_length, load_pieces, load_pallets, load_value, damage_photo, damage_note, broker_mc, carrier_mc, carrier_tractor, carrier_trailer, type_of_equipment, equipment_options, rate_confirmation, rate_pay, pay_advance, brokered_date, rated_miles, payment_reference, lading_number, alternate_reference, seal_number, load_start, load_end, lading_status, shipper_contact_uuid, consignee_contact_uuid, user_uuid, lading_status_updated, carrier_contact_uuid, load_cubes) VALUES ('5948128a-3cc4-41a8-bf73-47f6ade8b849', null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, 'null', null, null, 'null', null);",
"message": "OK"
},
{
"code": "200",
"uuid": "d8a173ba-f326-4ebc-bb7b-a4849756e957",
"name": "lading_tasks",
"sql": "INSERT INTO v_lading_tasks (lading_uuid, lading_task_uuid, contact_uuid, signature_uuid, scan_uuid, date, task_type, good_type, load_start, load_end, scan_document_uuid, task_note) VALUES ('5948128a-3cc4-41a8-bf73-47f6ade8b849', 'd8a173ba-f326-4ebc-bb7b-a4849756e957', null, null, null, null, null, null, null, null, null, null);",
"message": "OK"
}
],
"message": "OK"
}

```

This endpoint creates a lading.

### HTTP Request

`POST https://example.com/app/api/5/ladings/?key=<api_key>`

### JSON Request Body

<aside class="success"><code>{&quot;pro_bill&quot;:null,&quot;trip_number&quot;:null,&quot;partial_or_full&quot;:null,&quot;shipment_number&quot;:null,&quot;load_details&quot;:null,&quot;load_special_info&quot;:null,&quot;load_weight&quot;:null,&quot;load_weight_actual&quot;:null,&quot;load_length&quot;:null,&quot;load_pieces&quot;:null,&quot;load_pallets&quot;:null,&quot;load_value&quot;:null,&quot;damage_photo&quot;:null,&quot;damage_note&quot;:null,&quot;broker_mc&quot;:null,&quot;carrier_mc&quot;:null,&quot;carrier_tractor&quot;:null,&quot;carrier_trailer&quot;:null,&quot;type_of_equipment&quot;:null,&quot;equipment_options&quot;:null,&quot;rate_confirmation&quot;:null,&quot;rate_pay&quot;:null,&quot;pay_advance&quot;:null,&quot;brokered_date&quot;:null,&quot;rated_miles&quot;:null,&quot;payment_reference&quot;:null,&quot;lading_number&quot;:null,&quot;alternate_reference&quot;:null,&quot;seal_number&quot;:null,&quot;load_start&quot;:null,&quot;load_end&quot;:null,&quot;lading_status&quot;:null,&quot;shipper_contact_uuid&quot;:null,&quot;consignee_contact_uuid&quot;:null,&quot;user_uuid&quot;:null,&quot;lading_status_updated&quot;:null,&quot;carrier_contact_uuid&quot;:null,&quot;load_cubes&quot;:null,&quot;lading_tasks&quot;:[{&quot;contact_uuid&quot;:null,&quot;signature_uuid&quot;:null,&quot;scan_uuid&quot;:null,&quot;date&quot;:null,&quot;task_type&quot;:null,&quot;good_type&quot;:null,&quot;load_start&quot;:null,&quot;load_end&quot;:null,&quot;scan_document_uuid&quot;:null,&quot;task_note&quot;:null},{&quot;contact_uuid&quot;:null,&quot;signature_uuid&quot;:null,&quot;scan_uuid&quot;:null,&quot;date&quot;:null,&quot;task_type&quot;:null,&quot;good_type&quot;:null,&quot;load_start&quot;:null,&quot;load_end&quot;:null,&quot;scan_document_uuid&quot;:null,&quot;task_note&quot;:null},{&quot;contact_uuid&quot;:null,&quot;signature_uuid&quot;:null,&quot;scan_uuid&quot;:null,&quot;date&quot;:null,&quot;task_type&quot;:null,&quot;good_type&quot;:null,&quot;load_start&quot;:null,&quot;load_end&quot;:null,&quot;scan_document_uuid&quot;:null,&quot;task_note&quot;:null}],&quot;lading_logs&quot;:[]}</code></aside>

### URL Parameters

Parameter | Description
--------- | -----------
key | The API key

<aside class="notice">
See JSON value, types, and descriptions of <a href="http://ulaap.com:4567/#get-all-ladings">ladings</a>
</aside>

<aside class="warning">
The API will automatically populate the following fields, so, they are not to be sent in the POST request body: <code>consignee_name, consignee_locality, consignee_region, shipper_name, shipper_locality, shipper_region</code>   
</aside>





