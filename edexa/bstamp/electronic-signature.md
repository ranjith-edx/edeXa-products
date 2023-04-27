# Electronic Signature

{% hint style="info" %}
**MAINNET BASEURL**\
[https://api-edexagw.edexa.com/bstamp](https://api-edexagw.edexa.com/bstamp)/\
\
**TESTNET BASEURL**\
[https://api-edexagw.io-world.com/bstamp](https://api-edexagw.io-world.com/bstamp)/
{% endhint %}

{% swagger method="post" path="" baseUrl="hash" summary="Electronic Signature" %}
{% swagger-description %}
You have to pass your 

**token**

 via the 

**Authorization**

 parameter through the headers.
{% endswagger-description %}

{% swagger-parameter in="body" name="hash" type="String" %}
Hash value
{% endswagger-parameter %}

{% swagger-parameter in="body" name="filename" type="String" %}
Upload 

**xml**

 or 

**pdf**
{% endswagger-parameter %}

{% swagger-parameter in="body" name="latitude" type="String" %}
An optional parameter
{% endswagger-parameter %}

{% swagger-parameter in="body" name="longitude" type="String" %}
An optional parameter
{% endswagger-parameter %}

{% swagger-parameter in="body" name="description" type="String" %}
An optional parameter
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" required="true" type="String" %}
token
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="String" %}
An optional parameter
{% endswagger-parameter %}

{% swagger-parameter in="body" name="attachments" type="String" %}
A file
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-Type" required="true" type="String" %}
multipart/form-data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="align" type="String" %}
**top** - In PDF, add a watermark to the **header**,&#x20;

**bottom** - In PDF, add a watermark to the **footer**
{% endswagger-parameter %}

{% swagger-parameter in="body" name="isPrivate" type="Boolean" %}
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
        "id": "6409e64*********",
        "hash": "6d6db6c25*********************",
        "txid": "4c934966e102***********************",
        "code": "0da***",
        "filename": "Test.pdf"
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

{% swagger-response status="409: Conflict" description="Stamp already Exist." %}
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
