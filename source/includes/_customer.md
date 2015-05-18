# Customer

## Register a new customer account

> Request example

```json
{
    "password": "123456",
    "passwordConfirmation": "123456",
    "email": "ceble2@nexway.fr",
    "firstname": "Christophe",
    "lastname": "Eblé",
    "dob": "1974-11-18",
    "optinNewsletter": true,
    "optinSms": true,
    "billingAddress": {
        "street": "23 rue Auguste Edith",
        "street2": "Hameau de Pinchefalise, Clos de l'Estran",
        "city": "Boismont",
        "countryId": "FR",
        "postCode": "80230",
        "region": 80,
        "telephone": "0987654321"
    }
}
```

> Response example

```json
{
    "success": true,
    "storeId": "1",
    "oAuth": {
        "accessToken": "msjkizn62witmcuq3hs20igb91rf8y6c",
        "tokenSecret": "lyi29uy8oqq1vyyigx2ejfe60qfhc6sq"
    }
}
```

This endpoint registers a new master account, the consumer & access token are also created and linked to the newly created account.

<aside class="notice">When you want to pass credit card data to the API you have to use encryption.</aside>

### HTTP Request

`POST https://my.appstore.com/api/register`

### JSON Request Parameters

Parameter | Mandatory | Default | Description
--------- | --------- | ------- | -----------
disableValidation | no | none | Field(s) path(s) that you want validation to ignore ex: `["billingAddress/street", "dob"]`
email | yes | none | The customer username.
password | yes | none | Customer password.
passwordConfirmation | yes | none | Password confirmation.
firstname | yes | none | Customer firstname.
lastname | yes | none | Customer lastname.
dob | yes | none | Date of birth, ISO 8601 international date format YYYY-MM-DD.
optinNewsletter | no | none | Newsletter subscription flag.
optinSms | no | none | The user nickname.
billingAddress.street | yes | none | Address.
billingAddress.street2 | no | none | Complementary address.
billingAddress.city | yes | none | City.
billingAddress.countryId | yes | none | Country ID.
billingAddress.postCode | yes | none | Zip code.
billingAddress.region | no | none | Region code.
billingAddress.telephone | no | none | Phone number.

### Response Parameters

Parameter | Type | Description
--------- | ---- | -----------
success | boolean | If registration succeeded.
oAuth.accessToken | string | oAuth access token.
oAuth.tokenSecret | string | oAuth token secret.
oAuth.storeId | int | Store ID on which the user is registered.

### Possible errors

Code | Meaning
---- | -------
2000 | Email `%s` already exists
2001 | Invalid email or password

## Login

> Request example

```json
{
    "username": "mduplouy@nexway.com",
    "password": "password01!",
    "getTokens": true
}
```

> Response example

```json
{
    "success": true,
    "storeId": "1",
    "customer": {
        "firstname": "Jonathan",
        "lastname": "Gautheron",
        "dob": "17/07/1987"
    },
    "oAuth": {
        "accessToken": "7s3npv041cqjqsdu1jwdf7c3fzhiolv9",
        "tokenSecret": "zhnhazeeaz44jrxmekombu8nns76nzm0"
    },
    "childAccount": [{
        "accountId": 89,
        "firstname": "Wiktor",
        "dob": "19/07/2014"
    }, {
        "accountId": 90,
        "firstname": "Emilia",
        "dob": "28/11/1983"
    }],
    "billingAddress": {
        "street": "Lipowa 7",
        "street2": "",
        "city": "Zaborze",
        "countryId": "PL",
        "postCode": "42310"
    }
}
```

This endpoint logs in the user.

Rules :

- The kid firstname will be appended to the parent email address so it will remain unique (by ex. jgautheron+wiktor@nexway.com).
- The parent lastname will be used as the child lastname (mandatory for account creation).

<aside class="warning">The previous child registration behavior has been refactored in its entirety. The previous behaviour called the internal webservices to create the child account and then update it. The issue was that in a leap of faith, the method tried to get the Child ID in the headers, but for some reason sometimes it wasn't in the headers. 
The refactoring simply makes use of the model.</aside>

### HTTP Request

`GET https://my.appstore.com/api/login/index`

### JSON Request Parameters

Parameter | Mandatory | Default | Description
--------- | --------- | ------- | -----------
username | yes | none | The customer username.
password | yes | none | The customer password (plaintext).
getTokens | yes | none | Send back the oAuth tokens.

### Response Parameters

Parameter | Type | Description
--------- | ---- | -----------
success | boolean | If the login succeeded.
isPasswordReset | boolean | When customer has logged in using reset token.
storeId | int | Store ID on which the user is registered.
customer.firstname | string | The customer firstname.
customer.lastname | string | The customer lastname.
customer.dob | string | The customer birthday, dd/mm/yyyy format.
oAuth.accessToken | string | oAuth access token.
oAuth.tokenSecret | string | oAuth token secret.
childAccount.accountId | int | Child customer id.
childAccount.firstname | string | Child firstname.
childAccount.dob | string | Child birthday, dd/mm/yyyy format.
billingAddress.street | yes | none | Address.
billingAddress.street2 | no | none | Complementary address.
billingAddress.city | yes | none | City.
billingAddress.countryId | yes | none | Country ID.
billingAddress.postCode | yes | none | Zip code.
billingAddress.region | no | none | Region code.
billingAddress.telephone | no | none | Phone number.

## Update account

> Request example

```json
{
    "firstname": "Christophe",
    "lastname": "Eble",
    "email": "ceble@nexway.com",
    "dob": "1981-10-31",
    "password": "nexway",
    "passwordConfirmation": "nexway",
    "optinNewsletter": true,
    "optinSms": true,
    "billingAddress": {
        "street": "64, Rue RPC Gilbert",
        "street2": "",
        "city": "Asnières-Sur-Seine",
        "countryId": "FR",
        "postCode": "92600",
        "region": 80,
        "telephone": "0987654321"
    }
}
```

> Response example

```json
{
    "success": true
}
```

This endpoint updates the customer details.

### HTTP Request

`POST https://my.appstore.com/api/account/update`

### Auth Required

`YES`

### JSON Request Parameters

Parameter | Mandatory | Default | Description
--------- | --------- | ------- | -----------
customer.firstname | yes | none | The customer firstname.
customer.lastname | yes | none | The customer lastname.
customer.dob | yes | none | The customer birthday, dd/mm/yyyy format.
customer.password | yes | none | The customer birthday, dd/mm/yyyy format.
customer.passwordConfirmation | yes | none | The customer birthday, dd/mm/yyyy format.
customer.optinNewsletter | no | none | Newsletter subscription.
customer.optinSms | no | none | Accept SMS flag.
billingAddress.street | yes | none | Address.
billingAddress.street2 | no | none | Complementary address.
billingAddress.city | yes | none | City.
billingAddress.countryId | yes | none | Country ID.
billingAddress.postCode | yes | none | Zip code.
billingAddress.region | no | none | Region code.
billingAddress.telephone | no | none | Phone number.

### Response Parameters

Parameter | Type | Description
--------- | ---- | -----------
success | boolean | If the update succeeded.

## Reset the account password

> Request example

```json
{
    "email": "ceble@nexway.com",
    "dob": "1981-10-31"
}
```

> Response example

```json
{
    "success": true
}
```

This endpoint generates a temporary password which is sent by email to the customer. Once logged in the user can change his password.

### HTTP Request

`POST https://my.appstore.com/api/account/password/reset`

### Auth Required

`YES`

### Possible errors

Code | Meaning
---- | -------
3006 | Email address not found
3007 | Date of birth and email doesn't match

## Update the account password

> Request example

```json
{
    "oldPassword": "telechargement",
    "password": "nexway",
    "passwordConfirmation": "nexway"
}
```

> Response example

```json
{
    "success": true
}
```

This endpoint updates the account password by the given one.

### HTTP Request

`POST https://my.appstore.com/api/account/password/new`
tu
### Auth Required

`YES`

### JSON Request Parameters

Parameter | Mandatory | Default | Description
--------- | --------- | ------- | -----------
oldPassword | yes | none | Current account password.
password | yes | none | Customer password.
passwordConfirmation | yes | none | Password confirmation.

### Response Parameters

Parameter | Type | Description
--------- | ---- | -----------
success | boolean | If the update succeeded.

### Possible errors

Code | Meaning
---- | -------
1008 | Passwords don't match
3008 | Current password does not match entered one

## Inventory

> Response example

```json
{
    "inventory": {
        "item": [{
            "sku": "TreaturesUOne",
            "name": "TreaturesUnlock",
            "priceFormatted": "€2.99",
            "price": 2.989996098,
            "currency": "EUR",
            "order": {
                "orderId": "3400000011",
                "orderDate": "20150518 06:56:16",
                "orderTimestamp": 1431932176
            }
        }],
        "app": [{
            "sku": "com.pepworks.pepthedragon",
            "name": "PEP The Dragon",
            "priceFormatted": "€1.84",
            "price": 1.83531531,
            "currency": "EUR",
            "order": {
                "orderId": "3400000012",
                "orderDate": "20150518 07:20:54",
                "orderTimestamp": 1431933654
            },
            "publisherName": "Pepworks",
            "packageName": "com.pepworks.pepthedragon",
            "apk": "http://cdn.mobile.nexway.com/com.pepworks.pepthedragon-1-enc.apk",
            "apkEncrypted": true,
            "version": "1",
            "rating": 0,
            "nbReviews": 0,
            "versionCode": 1,
            "versionLabel": "1.0",
            "medias": {
                "image": "http://cdn.mobile.nexway.com/media/catalog/product/i/c/icon_31_5.png"
            },
            "apkHashMac": "62038f6dd3410dc3cdd1238b818128bb865303e6"
        }]
    }
}
```

This endpoint retrieves the items purchased by the customer (apps, in-apps).

### HTTP Request

`GET https://my.appstore.com/api/account/inventory`

### Auth Required

`YES`

### Request Parameters

Parameter | Mandatory | Default | Description
--------- | --------- | ------- | -----------
storeId | yes | none | Store ID on which the user is registered.
