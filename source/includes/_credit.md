# Credit

## Get the available credit packs

> Response example

```json
{
    "packs": [{
        "sku": "piggy-pack-1",
        "formatedPrice": "$10.00",
        "price": 10,
        "currencySymbol": "USD",
        "name": "Piggy Pack 1"
    }, {
        "sku": "piggy-pack-2",
        "formatedPrice": "$30.00",
        "price": 30,
        "currencySymbol": "USD",
        "name": "Piggy Pack 2"
    }, {
        "sku": "piggy-pack-3",
        "formatedPrice": "$50.00",
        "price": 50,
        "currencySymbol": "USD",
        "name": "Piggy Pack 3"
    }]
}
```

This endpoint retrieves the available credit packs.

### HTTP Request

`GET https://my.appstore.com/api/payment/credit/list`

### Auth Required

`YES`

## Recharge credit

> Add credit to balance using a credit card

```json
{
    "sku": "piggy-pack-1",
    "to": "42",
    "paymentDetails": {
        "paymentMethod": "WorldPay/visa",
        "ccEncryptedData": "yP7dHxEid8DYrjrOafmk7Tbz69LuiPemL..",
        "ccEncryptionToken": "a9488248-2dc9-4cfd-b048-26b5c316c431"
    }
}
```

> Add credit to balance using an agreement ID

```json
{
    "sku": "piggy-pack-1",
    "to": "42",
    "agreementId": "aad0d7d8-df0b-11e2-acf0-de50000001ff"
}
```

> Response example

```json
{
    "success": true,
    "message": "",
    "status": "complete",
    "orderId": "100000188",
    "orderDate": "20130702 05:35:03",
    "creditInfo": {
        "label": "Customer Credit",
        "balance": 60,
        "balanceFormatted": "$60.00",
        "balanceCurrency": "USD"
    }
}
```

This endpoint recharges credit using a regular or saved payment method.

### HTTP Request

`POST https://my.appstore.com/api/payment/credit/add`

### Auth Required

`YES`
