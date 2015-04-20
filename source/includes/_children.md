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