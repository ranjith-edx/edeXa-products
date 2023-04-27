---
description: "Apart from the web interface, work.edexa.com's blockchain stamping functionality is also possible through an API interaction.  In order to get access to our API please\_create an account."
---

# Authentication

{% tabs %}
{% tab title="Sandbox" %}
[https://universe.io-world.com/apis](https://universe.io-world.com/apis)
{% endtab %}

{% tab title="Live" %}
[https://universe.edexa.com/apis](https://universe.io-world.com/apis)
{% endtab %}
{% endtabs %}

{% hint style="info" %}
The **Sandbox** and **Live** are the link of edeXa ecosystem from where you can get your secret id and client id.

The **Sandbox** and **Live** also provides you the feature to check the api working and their response from web.
{% endhint %}

{% hint style="info" %}
**MAINNET BASEURL**\
[https://api-edexagw.edexa.com/bstamp](https://api-edexagw.edexa.com/bstamp)/\
\
**TESTNET BASEURL**\
[https://api-edexagw.io-world.com/bstamp](https://api-edexagw.io-world.com/bstamp)/
{% endhint %}



{% swagger method="post" path="" baseUrl="authenticate" summary="Authenticate" expanded="false" %}
{% swagger-description %}
The following endpoint is used in order to authenticate with our service. For security reasons, the registered user will receive a client id and secret key which will be used in order to authenticate.

If you are already registered you can get your API credentials [https://accounts.edexa.com/](https://accounts.edexa.com/)


{% endswagger-description %}

{% swagger-parameter in="header" name="client-id" required="true" type="String" %}
3e03130f************
{% endswagger-parameter %}

{% swagger-parameter in="header" name="secret-key" required="true" type="String" %}
D038C*************************************************************
{% endswagger-parameter %}

{% swagger-response status="404: Not Found" description="User Not Found" %}
```json
{
    "status": 404,
    "message": "User Not Found"
}
```
{% endswagger-response %}

{% swagger-response status="200: OK" description="Success Response" %}
<pre class="language-json"><code class="lang-json">{
<strong>    "status": 200,
</strong>    "message": "Logged in successfully",
    "data": {
        "token": "eyJhbG***********.eyJzdWIiOiJVMkZzZE***********************",
        "_id": "6135*************",
        "name": "John Doe",
        "username": "John",
        "email": "j*****@gmail.com",
        "status": 1,
        "profilePicture": "",
        "loginType": "social",
        "refreshToken": "eyJhbG***********.eyJzdWIiOiJVMkZzZE*****************",
        "viewType": 0,
        "watermark": 0,
        "align": "top"
    }
}
</code></pre>
{% endswagger-response %}

{% swagger-response status="500: Internal Server Error" description="Some Technical issue occurred." %}
```javascript
{
    "status": 500,
    "message": "Something went wrong, please try again"
}{
    "status": 500,
    "message": "Something went wrong, please try again"
}
Some Technical issue occurred.
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="" baseUrl="user-profile" summary="User Profile" %}
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

{% swagger-response status="200: OK" description="Success Response" %}
```json
{
   "status": 200,
    "message": "Get details successfully",
    "data": {
        "first_name": "e",
        "last_name": "Jhon",
        "username": "Doe",
        "email": "john@gmail.com",
        "profilePic": "Profile image",
        "thumbProfile": "Thumb Profile image",
        "_id": "630************",
        "userId": "3e03130f*******************",
        "gender": "Male",
        "status": 1,
        "loginType": "normal",
        "updatedAt": "2022-04-27T12:15:31.283Z",
        "isEmailVerified": 1,
        "dob": "2010-12-31T18:30:00.000Z",
        "kycApproved": 0,
        "twoAuth": false,
        "viewType": 0,
        "watermark": 0,
        "align": "top",
        "language": "EN"
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

{% swagger-response status="500: Internal Server Error" description="Some Technical issue occurred." %}
```javascript
{
    "status": 500,
    "message": "Something went wrong, please try again"
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="put" path="" baseUrl="account-preference" summary="Update Account Preference" %}
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

{% swagger-parameter in="body" name="viewType" type="String" %}
**0**

 for 

_PDF_

, 

**1**

 for 

_JSON_

 & 

**2**

 for none.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="watermark" type="String" %}
**0**

 for 

_no watermark_

 & 

**1**

 for 

_watermark in pdf_

.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="align" type="String" %}
**top**

 for watermark in 

_header_

, 

**bottom**

 for watermark in 

_bottom._
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Updated Successfully" %}
```json
{
    "status": 200,
    "message": "Preference updated successfully",
    "data": {
        "viewType": 1,
        "watermark": 0,
        "align": "top"
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

{% swagger-response status="500: Internal Server Error" description="Some Technical issue occurred." %}
```javascript
{
    "status": 500,
    "message": "Something went wrong, please try again"
}
```
{% endswagger-response %}
{% endswagger %}

