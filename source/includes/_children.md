# Children

## Get the children's wishlist

> Response example

```json
{
    "children": [{
        "name": "Matt",
        "dob": "2006-08-01",
        "accountId": "1139684",
        "count": 0
    }]
}
```

This endpoint retrieves the children's wishlist.  

### HTTP Request

`GET https://my.appstore.com/api/wishlist/children`

### Auth Required

`YES`

## Get the available payment methods

> Response example

```json
{
    "credit": {
        "label": "Customer Credit",
        "balance": 4.96,
        "balanceFormatted": "$4.96",
        "balanceCurrency": "USD",
        "enabled": true,
        "ceilingType": "daily",
        "ceilingValue": 25,
        "ceilingValueFormatted": "$25.00"
    }
}
```

This endpoint retrieves the payment methods available to the children account.

### HTTP Request

`GET https://my.appstore.com/api/payment/wallet/list`

### Auth Required

`YES`

## Get the available children credits

> Response example

```json
{
    "children": [{
        "name": "Victor",
        "dob": "2007-05-06",
        "accountId": "3529",
        "label": "Customer Credit",
        "balance": 395.82707925,
        "balanceFormatted": "€395.83",
        "balanceCurrency": "EUR",
        "enabled": true
    }, {
        "name": "Eléonore",
        "dob": "2005-11-14",
        "accountId": "3532",
        "label": "Customer Credit",
        "balance": 5.52280315,
        "balanceFormatted": "€5.52",
        "balanceCurrency": "EUR",
        "enabled": true
    }]
}
```

This endpoint retrieves the children credits.

### HTTP Request

`GET https://my.appstore.com/api/payment/wallet/children/list`

### Auth Required

`YES`

## Child account registration

> Request example

```json
{
    "dob": "06/02/1977",
    "firstname": "Chris"
}
```

> Response example

```json
{
    "success": true,
    "accountId": 102
}
```

This endpoint registers an account for a child.

Rules :

- The child firstname will be appended to the parent email address so it will remain unique (by ex. jgautheron+wiktor@nexway.com).
- The parent lastname will be used as the child lastname (mandatory for account creation).

<aside class="warning">The previous child registration behavior has been refactored in its entirety. The previous behaviour called the internal webservices to create the child account and then update it. The issue was that in a leap of faith, the method tried to get the Child ID in the headers, but for some reason sometimes it wasn't in the headers. 
The refactoring simply makes use of the model.</aside>

### HTTP Request

`POST https://my.appstore.com/api/child/register`

### JSON Request Parameters

Parameter | Mandatory | Default | Description
--------- | --------- | ------- | -----------
dob | yes | none | Date of birth, ISO 8601 international date format YYYY-MM-DD.
firstname | yes | none | Customer firstname.

### Response Parameters

Parameter | Type | Description
--------- | ---- | -----------
success | boolean | If registration succeeded.
accountId | int | The newly created customer Id if succeeded.

## Child account detail

> Response example

```json
{
    "firstname": "agathe",
    "dob": "18/09/1977",
    "avatar": "",
    "balance": 0,
    "orderHistory": [{
        "orderId": 2,
        "date": "18/12/2012",
        "amount": "3.99 €",
        "content": [{
            "sku": "123456789",
            "name": "Power up item",
            "unitPrice": "3.99 €",
            "qty": 1
        }]
    }]
}
```

This endpoint retrieves the child account details.

### HTTP Request

`GET https://my.appstore.com/api/child/account`

### Auth Required

`YES`

### Query Parameters

Parameter | Mandatory | Default | Description
--------- | --------- | ------- | -----------
accountId | yes | none | The child account ID.

### Response Parameters

Parameter | Type | Description
--------- | ---- | -----------
firstname | string | If registration succeeded.
dob | string | The newly created customer Id if succeeded.
avatar | string | The newly created customer Id if succeeded.
balance | string | The newly created customer Id if succeeded.
orderHistory[] | array | List of orders.
orderHistory[].orderId | string | Order ID.
orderHistory[].date | string | Date of order (DD/MM/YYYY).
orderHistory[].amount | string | Total order amount localized with currency symbol.
orderHistory[].content[] | array | List of products.
orderHistory[].content[].sku | string | Product SKU.
orderHistory[].content[].name | string | Product name.
orderHistory[].content[].unitPrice | string | Unit price localized with currency symbol.
orderHistory[].content[].qty | int | Ordered quantity.

## Get the available children credits

> Response example

```json
{
    "children": [{
        "name": "Victor",
        "dob": "2007-05-06",
        "accountId": "3529",
        "label": "Customer Credit",
        "balance": 395.82707925,
        "balanceFormatted": "€395.83",
        "balanceCurrency": "EUR",
        "enabled": true
    }, {
        "name": "Eléonore",
        "dob": "2005-11-14",
        "accountId": "3532",
        "label": "Customer Credit",
        "balance": 5.52280315,
        "balanceFormatted": "€5.52",
        "balanceCurrency": "EUR",
        "enabled": true
    }]
}
```

This endpoint retrieves the children credits.

### HTTP Request

`GET https://my.appstore.com/api/payment/wallet/children/list`

### Auth Required

`YES`

## Delete child account

> Request example

```json
{
    "accountId": 4
}
```

> Response example

```json
{
    "success": true
}
```

This endpoint deletes a child account.

### HTTP Request

`POST https://my.appstore.com/api/child/delete`

## Update child account

> Request example

```json
{
    "accountId": 4,
    "firstname": "Ania",
    "dob": "2005-07-20"
}
```

> Response example

```json
{
    "success": true
}
```

This endpoint updates a child account.

### HTTP Request

`POST https://my.appstore.com/api/child/update`

### Auth Required

`YES`

## Configure the piggy bank

> Request example

```json
{
    "to": "telechargement",
    "enabled": "nexway",
    "ceiling": {
        "type": "weekly",
        "value": "15"
    }
}
```

> Response example

```json
{
    "success": true
}
```

This endpoint configures the piggy bank of the given child account.

### HTTP Request

`POST https://my.appstore.com/api/account/credit/setup`

### JSON Request Parameters

Parameter | Mandatory | Default | Description
--------- | --------- | ------- | -----------
to | yes | none | Child account ID.
enabled | no | true | Enable the piggy for the given account.
ceiling.type | no | none | Ceiling type: "daily", "weekly" or "monthly".
ceiling.value | yes | none | Ceiling value, if set to zero, it will remove the ceiling.

### Response Parameters

Parameter | Type | Description
--------- | ---- | -----------
success | boolean | If the update succeeded.

### Possible errors

Code | Meaning
---- | -------
0004 | Invalid Sub Account
0007 | The account has no active credit