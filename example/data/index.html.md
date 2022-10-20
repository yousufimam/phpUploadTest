---
title: API Reference

language_tabs:
  - shell
  - ruby
  - python
  - javascript

footer:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/shamin/greenboard'>Documentation Powered by Greenboard</a>

includes:
  - errors

search: true

attachments:
  - "./kaispe_logo.png"
---

# Introduction

Welcome to the Proof Of Delivery API! You can use our API to access our API endpoints, which can get information on various invoice records, profiles of driver in our database.

We have language bindings in Shell, Ruby, Python, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Greenboard](https://github.com/shamin/greenboard). Feel free to edit it and use it as a base for your own API's documentation.



# Invoice Records

## Get All Invoices

```ruby
require "uri"
require "net/http"

url = URI("https://proof-of-delivery-bsi.herokuapp.com/Auth")

https = Net::HTTP.new(url.host, url.port)
https.use_ssl = true

request = Net::HTTP::Get.new(url)

response = https.request(request)
puts response.read_body

```

```python
import requests

url = "https://proof-of-delivery-bsi.herokuapp.com/Auth"

payload={}
headers = {}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)
```

```shell
curl "https://proof-of-delivery-bsi.herokuapp.com/Auth"
```

```javascript
var requestOptions = {
  method: 'GET',
  redirect: 'follow'
};

fetch("https://proof-of-delivery-bsi.herokuapp.com/Auth?truckId=TR", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> The above command returns JSON structured like this:

```json
{
    "context": "",
    "value": [
        {
            "_id": "634e5233d4107fa44741cc70",
            "invoice": "AR028288_SO-Inv",
            "truckId": "TR",
            "deliveryDate": "2022-01-26T12:00:00.000Z",
            "dataAreaId": "bsi",
            "company": "BSI Steel (PTY) LTD",
            "salesUnit": "KG",
            "invoiceDate": "2022-01-19T12:00:00.000Z",
            "invoiceAmount": "0",
            "invoiceAmountMST": "0",
            "address": "73 Sardine Road\nGermiston\n1422",
            "grossWeight": "2300",
            "currencyCode": "",
            "customerName": "",
            "signatureImageUrl": "",
            "nameOfReceiver": "sign",
            "commentByReciver": "hey",
            "actualDateOfDelivery": "sgsdhrh",
            "deliveryStatus": "delivered",
            "latitude": "24.922901096541818",
            "longitude": "67.10812835212685",
            "invoiceDetails": [
                {
                    "invoice": "AR028288_SO-Inv",
                    "truckId": "TR",
                    "deliveryDate": "2022-01-26T12:00:00.000Z",
                    "dataAreaId": "bsi",
                    "companyName": "BSI Steel (PTY) LTD",
                    "invoiceAmountMST": "0",
                    "salesUnit": "KG",
                    "invoiceDate": "2022-01-19T12:00:00.000Z",
                    "invoiceAmount": "0",
                    "address": "73 Sardine Road\nGermiston\n1422",
                    "odataetag": "",
                    "name": "Slit Galvanised ISQ 230 Prime Z275  132.0x0.96",
                    "grossWeight": "2300",
                    "currencyCode": "ZAR",
                    "customerName": "Teichmann Steel (Pty) Ltd",
                    "itemId": "0012580",
                    "qty": "6786",
                    "_id": "634e5233d4107fa44741cc71"
                }
            ],
            "__v": 0,
            "imageRef": "634e81d7567379202ef8120a"
        }
    ]
}
```

This endpoint retrieves all invoices.

### HTTP Request

`GET https://proof-of-delivery-bsi.herokuapp.com/Auth`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
truckId |  | If value is given, the result will only consists of the invoices of the this specific truck id .


## Post invoice data in bulk

```ruby
require "uri"
require "json"
require "net/http"

url = URI("https://proof-of-delivery-bsi.herokuapp.com/Auth/new")

https = Net::HTTP.new(url.host, url.port)
https.use_ssl = true

request = Net::HTTP::Post.new(url)
request["Content-Type"] = "application/json"
request.body = JSON.dump([ data to insert ])

response = https.request(request)
puts response.read_body
```

```python
import requests
import json

url = "https://proof-of-delivery-bsi.herokuapp.com/Auth/new"

payload = json.dumps([
    data to insert 
])
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

```shell
curl --location --request POST 'https://proof-of-delivery-bsi.herokuapp.com/Auth/new' \
--header 'Content-Type: application/json' \
--data-raw '[
        data to insert
        ]'
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Content-Type", "application/json");

var raw = JSON.stringify([
  data to insert 
]);

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://proof-of-delivery-bsi.herokuapp.com/Auth/new", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> The above command returns status code message like this:

```json
Created
```

This endpoint is used to insert invoices in bulk quantity.


### HTTP Request

`POST https://proof-of-delivery-bsi.herokuapp.com/Auth/new`

### Body Parameters

Parameter | Description
--------- | -----------
array | Consists of list of invoices 




# Driver Profile

## Create profile

```ruby
require "uri"
require "json"
require "net/http"

url = URI("https://proof-of-delivery-bsi.herokuapp.com/profile/create")

https = Net::HTTP.new(url.host, url.port)
https.use_ssl = true

request = Net::HTTP::Post.new(url)
request["Content-Type"] = "application/json"
request.body = JSON.dump({
  data to insert in json
})

response = https.request(request)
puts response.read_body

```

```python
import requests
import json

url = "https://proof-of-delivery-bsi.herokuapp.com/profile/create"

payload = json.dumps({
  data to insert in json
})
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)

```

```shell
curl --location --request POST 'https://proof-of-delivery-bsi.herokuapp.com/profile/create' \
--header 'Content-Type: application/json' \
--data-raw '{
    data to insert in json
}'
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Content-Type", "application/json");

var raw = JSON.stringify({
  data to insert in json
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://proof-of-delivery-bsi.herokuapp.com/profile/create", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> The above command returns status code message like this:

```json
  Created
```

This endpoint is used to create a driver profile

### HTTP Request

`POST https://proof-of-delivery-bsi.herokuapp.com/profile/create`

### Body Parameters

Parameter | Description
--------- | -----------
name | Should be given in string
password | Should be given in string
truckId | Should be string and unique
phoneNumber | Should be given in string
address | Should be given in string


## Get the driver profile

```ruby
require "uri"
require "net/http"

url = URI("https://proof-of-delivery-bsi.herokuapp.com/profile/:truckId")

https = Net::HTTP.new(url.host, url.port)
https.use_ssl = true

request = Net::HTTP::Get.new(url)

response = https.request(request)
puts response.read_body
```

```python
import requests

url = "https://proof-of-delivery-bsi.herokuapp.com/profile/:truckId"

payload={}
headers = {}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)

```

```shell
curl --location --request GET 'https://proof-of-delivery-bsi.herokuapp.com/profile/:truckId'
```

```javascript
var requestOptions = {
  method: 'GET',
  redirect: 'follow'
};

fetch("https://proof-of-delivery-bsi.herokuapp.com/profile/:truckId", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> The above command returns JSON structured like this:

```json
{
    "_id": "object Id",
    "name": "Name of driver",
    "password": "Password of truck driver",
    "truckId": "Truck id of driver",
    "phoneNumber": "phone number of driver",
    "address": "address of driver"
}
```

This endpoint is used to get the specific driver profile


### HTTP Request

`GET https://proof-of-delivery-bsi.herokuapp.com/profile/:truckId`

### URL Parameters

Parameter | Description
--------- | -----------
truckId | The truck id of the driver should be given 



## Update the driver profile

```ruby
require "uri"
require "json"
require "net/http"

url = URI("https://proof-of-delivery-bsi.herokuapp.com/profile/:truckId")

http = Net::HTTP.new(url.host, url.port);
request = Net::HTTP::Patch.new(url)
request["Content-Type"] = "application/json"
request.body = JSON.dump({
  update fields in json
})

response = http.request(request)
puts response.read_body
```

```python
import requests
import json

url = "https://proof-of-delivery-bsi.herokuapp.com/profile/:truckId"

payload = json.dumps({
  update fields in json
})
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("PATCH", url, headers=headers, data=payload)

print(response.text)

```

```shell
curl --location --request PATCH 'https://proof-of-delivery-bsi.herokuapp.com/profile/:truckId' \
--header 'Content-Type: application/json' \
--data-raw '{
  update fields in json
}'
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Content-Type", "application/json");

var raw = JSON.stringify({
  update fields in json

});

var requestOptions = {
  method: 'PATCH',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://proof-of-delivery-bsi.herokuapp.com/profile/TR1", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> The above command returns JSON structured like this:

```json
{ 
  "message": "User updated successfully"
}
```

This endpoint is used to update the specific driver profile


### HTTP Request

`PATCH https://proof-of-delivery-bsi.herokuapp.com/profile/:truckId`

### URL Parameters

Parameter | Description
--------- | -----------
truckId | The truck id of the driver should be given


### Body Parameters

Parameter | Description
--------- | -----------
name | Should be given in string
password | Should be given in string
truckId | Should be string and unique
phoneNumber | Should be given in string
address | Should be given in string



## Update the profile image

```ruby
require "uri"
require "net/http"

url = URI("https://proof-of-delivery-bsi.herokuapp.com/profile/image")

https = Net::HTTP.new(url.host, url.port)
https.use_ssl = true

request = Net::HTTP::Post.new(url)
form_data = [
  data to insert
]
request.set_form form_data, 'multipart/form-data'
response = https.request(request)
puts response.read_body

```

```python
import requests

url = "https://proof-of-delivery-bsi.herokuapp.com/profile/image"

payload={ text fields to add }
files=[
  file fields to add
]
headers = {}

response = requests.request("POST", url, headers=headers, data=payload, files=files)

print(response.text)

```

```shell
curl --location --request POST 'https://proof-of-delivery-bsi.herokuapp.com/profile/image' \
--form 'data to add'\
```

```javascript
var formdata = new FormData();
formdata.append(data to add)

var requestOptions = {
  method: 'POST',
  body: formdata,
  redirect: 'follow'
};

fetch("https://proof-of-delivery-bsi.herokuapp.com/profile/image", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> The above command returns JSON structured like this:

```json
{ 
  "message": "User updated successfully",
  "url": "url of image"
}
```

This endpoint is used to update the specific driver profile image


### HTTP Request

`POST https://proof-of-delivery-bsi.herokuapp.com/profile/image`

### Body Parameters

Parameter | Description
--------- | -----------
profileImage | Should be given in file type
truckId | Should be string




#AUTH
## Login the driver profile

```ruby
require "uri"
require "json"
require "net/http"

url = URI("https://proof-of-delivery-bsi.herokuapp.com/Auth")

https = Net::HTTP.new(url.host, url.port)
https.use_ssl = true

request = Net::HTTP::Post.new(url)
request["Content-Type"] = "application/json"
request.body = JSON.dump({
  "truckId": "truck id",
  "password": "password of driver"
})

response = https.request(request)
puts response.read_body

```

```python
import requests
import json

url = "https://proof-of-delivery-bsi.herokuapp.com/Auth"

payload = json.dumps({
  "truckId": "truck id",
  "password": "password of driver"
})
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)

```

```shell
curl --location --request POST 'https://proof-of-delivery-bsi.herokuapp.com/Auth' \
--header 'Content-Type: application/json' \
--data-raw '{
  "truckId": "truck id",
  "password": "password of driver"
}'
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Content-Type", "application/json");

var raw = JSON.stringify({
  "truckId": "truck id",
  "password": "password of driver"
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://proof-of-delivery-bsi.herokuapp.com/Auth", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> The above command returns JSON structured like this:

```json
{
  "Success": true,
  "TruckID": "truckId",
  "Message": "Successfully Login."
}
```

This endpoint is used to login the driver


### HTTP Request

`POST https://proof-of-delivery-bsi.herokuapp.com/Auth`

### Body Parameters

Parameter | Description
--------- | -----------
truckId | Should be string and unique
password | Should be given in string




## Upload the Signed Image

```ruby
require "uri"
require "net/http"

url = URI("https://proof-of-delivery-bsi.herokuapp.com/Auth/upload")

https = Net::HTTP.new(url.host, url.port)
https.use_ssl = true

request = Net::HTTP::Post.new(url)
form_data = [ data to insert ]
request.set_form form_data, 'multipart/form-data'
response = https.request(request)
puts response.read_body
```

```python
import requests

url = "https://proof-of-delivery-bsi.herokuapp.com/Auth/upload"

payload={
  data to insert
}
files=[

]
headers = {}

response = requests.request("POST", url, headers=headers, data=payload, files=files)

print(response.text)

```

```shell
curl --location --request POST 'https://proof-of-delivery-bsi.herokuapp.com/Auth/upload' \
--form 'field to update'\
```

```javascript
var formdata = new FormData();
formdata.append(field to update)

var requestOptions = {
  method: 'POST',
  body: formdata,
  redirect: 'follow'
};

fetch("https://proof-of-delivery-bsi.herokuapp.com/Auth/upload", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> The above command returns JSON structured like this:

```json
{
  "successfull": true
}
```

This endpoint is used to update the invoice record and save the image string to db


### HTTP Request

`POST https://proof-of-delivery-bsi.herokuapp.com/Auth/upload`

### Body Parameters

Parameter | Description
--------- | -----------
Name | Should be string 
Comments | Should be given in string
DataAreaId | Should be given in string
TruckId | Should be given in string
FileName | Should be given in string
FileDate | Should be given in string
InvoiceNo | Should be given in string
actualDateOfDelivery | Should be given in string
