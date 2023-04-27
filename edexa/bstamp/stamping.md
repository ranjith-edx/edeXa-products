---
description: To store
---

# Stamping

Here is the list of **stamping api** through which user can post a hash on the blockchain of his choice.

{% hint style="info" %}
**MAINNET BASEURL**\
[https://api-edexagw.edexa.com/bstamp](https://api-edexagw.edexa.com/bstamp)/\
\
**TESTNET BASEURL**\
[https://api-edexagw.io-world.com/bstamp](https://api-edexagw.io-world.com/bstamp)/
{% endhint %}

{% swagger method="post" path="" baseUrl="hash" summary="Add Stamp" %}
{% swagger-description %}
This endpoint will allow you to store metadata to your stamping: _hash_, _filename_, _latitude_, _longitude, isPrivate, description and type ._

The _latitude, longitude, description and type are optional fields._

You have to pass your **token** via the **Authorization** parameter through the headers.
{% endswagger-description %}

{% swagger-parameter in="body" name="hash" required="true" type="String" %}
Hash value
{% endswagger-parameter %}

{% swagger-parameter in="body" name="filename" required="true" type="String" %}
Name of file which you want to stamp on blockchain.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" required="true" type="String" %}
token
{% endswagger-parameter %}

{% swagger-parameter in="body" name="isPrivate" required="true" type="Boolean" %}
You want to store it on 

**public**

 

**blockchain**

 or 

**private**

 

**blockchain**

.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Success Response" %}
```json
{
    "status": 200,
    "message": "Your hash is created with block chain",
    "data": {
        "id": "618bd1************",
        "hash": "6d6db6c2584******************",
        "txid": "b40ff5f7b3a90************************",
        "code": "c28***",
        "filename": "test.pdf"
    }
}
```
{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="Token passed in headers not valid" %}
```javascript
{
    "status": 401,
    "message": "Invalid auth token"
}
```
{% endswagger-response %}

{% swagger-response status="409: Conflict" description="Already existing on blockchain." %}
```json
{
    "status": 409,
    "message": "Stamp Already Exists"
}
```
{% endswagger-response %}

{% swagger-response status="500: Internal Server Error" description="Some Technical issue occurred." %}
```json
{
    "status": 500,
    "message": "Something went wrong, please try again"
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="" baseUrl="hash?page=1&limit=10" summary="Stamp List" %}
{% swagger-description %}
This API fetches the stamp data saved against a client id and secret key used by user during authentication.\
The response will have transaction id, blockchain id and other data fields in response.

You have to pass your **token** via the **Authorization** parameter through the headers.
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" required="true" type="String" %}
token
{% endswagger-parameter %}

{% swagger-parameter in="query" name="page" type="Number" required="true" %}
Page number
{% endswagger-parameter %}

{% swagger-parameter in="query" name="limit" type="Number" required="true" %}
Limit per page
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Success Response" %}
```json
{
     "status": 200,
    "message": "Get details successfully",
    "data": {
        "count": 1,
        "files": [
         {
                "_id": "63ea***********",
                "userId": "630625*********",
                "clientId": "3e03130f*****************",
                "blockchainId": "ac31800d*********************",
                "name": "abc.png",
                "txId": "fd009477ea9*******************",
                "hash": "6d6db6c25a4as1a********************",
                "type": "0",
                "code": "e6a0fd",
                "originalDocHash": "6d6db6c25a4as1*************",
                "isEsign": false,
                "isPrivateBc": true,
                "createdAt": "2023-02-13T12:44:55.381Z",
                "updatedAt": "2023-02-13T12:44:56.952Z"
            },
     ],
   }
}
```
{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="Token passed in headers not valid" %}
```javascript
{
    // Response
}
```
{% endswagger-response %}

{% swagger-response status="404: Not Found" description="User doesn't exist." %}
```javascript
{
    "status": 404,
    "message": "User does not exist"
}
```
{% endswagger-response %}

{% swagger-response status="500: Internal Server Error" description="Some technical issue occurred." %}
```json
{
    "status": 500,
    "message": "Something went wrong, please try again"
}{
    "status": 500,
    "message": "Something went wrong, please try again"
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="" baseUrl="hash?id=a1b2c3" summary="Stamp Details" %}
{% swagger-description %}
The **GET Stamp** API call will check whether a hash has been posted on the selected blockchain. This endpoint can also be used to fetch the transaction id, hash details, or other metadata associated with the stamp that you have created.

You have to pass your **token** via the **Authorization** parameter through the headers.
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" required="true" type="String" %}
token
{% endswagger-parameter %}

{% swagger-parameter in="query" name="id" required="true" type="String" %}
**Code**

 or 

**Hash**

 or 

**txId**
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Success Response" %}
```json
{
    "status": 200,
    "message": "Get details successfully",
    "data": {
        "hash": "6d6db6c25*******************************",
        "originalDocHash": "6d6db6c25***************************",
        "metaData": [
            {
                "latitude": "79.08",
                "longitude": "24.22",
                "description": "hello world"
            }
        ],
        "filename": "abc.png",
        "type": "0",
        "txid": "fd009477ea9************************************",
        "timestamp": "2023-02-13T12:44:55.381Z",
        "code": "e6a***",
        "username": "Jhon Doe",
        "userVerify": 0,
        "isEsign": false,
        "isPrivateBc": true
    }
}
```
{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="Token passed in headers not valid" %}
```json
{
    "status": 401,
    "message": "Invalid auth token"
}
```
{% endswagger-response %}

{% swagger-response status="404: Not Found" description="No Stamp exist" %}
```json
{
    "status": 404,
    "message": "Stamp does not exist"
}
```
{% endswagger-response %}

{% swagger-response status="404: Not Found" description="User doesn't exist." %}
```javascript
{
    "status": 404,
    "message": "User does not exist"
}
```
{% endswagger-response %}

{% swagger-response status="500: Internal Server Error" description="Some Technical issue occurred." %}
```json
{
    "status": 500,
    "message": "Something went wrong, please try again"
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="" baseUrl="multi-stamp" summary="Multiple Hash Stamping" %}
{% swagger-description %}
You have to pass your 

**token**

 via the 

**Authorization**

 parameter through the headers.
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" required="true" type="String" %}
token
{% endswagger-parameter %}

{% swagger-parameter in="body" name="file" type="String" required="true" %}
File name which you want to stamp.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="hash" type="String" required="true" %}
The hash value.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="isPrivate" type="Boolean" required="true" %}
You want to store it on 

**public**

 

**blockchain**

 or 

**private**

 

**blockchain**

.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Success Response" %}
```javascript
{
    "status": 200,
    "message": "Hash stamped successfully",
    "data": [
        {
            "id": "62aaXXXXXXXXXXXX",
            "hash": "6d6db6c25841aaaXXXXXXXXXXXX",
            "txid": "351f5a33781f7XXXXXXXXXXXX"
        }
    ]
}
```
{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="Token passed in headers not valid" %}
```javascript
{
    "status": 401,
    "message": "Invalid auth token"
}
```
{% endswagger-response %}

{% swagger-response status="500: Internal Server Error" description="Some Technical issue occurred." %}
```javascript
{
    "status": 500,
    "message": "Something went wrong, please try again"
}
```
{% endswagger-response %}
{% endswagger %}
