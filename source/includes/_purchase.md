# Purchase

## Get a payment token

> Response example

```json
{
    "token": "f48a9c38-2e25-4957-9a27-dfabbaa59957",
    "publicKey": "-----BEGIN PUBLIC KEY-----
    MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAy3WpP9 / hD3sxUeTr6ZMx + hxE9IoUapaEjE5Yo + GxbQqATKfNHjjKMtYzDiSrlxJYHD7FompVZpMT204beu3m
    4 t1EbPsMp2 / pYa64kflb5hBfWS6tdDczETh0ibeKwLRb2asE8tPRqZlt9M024Pv9
    2 jlCb76hHaDXEHV1PsDObPO7Mq6JFxE01zXgMg6YfIw / 22 Jiv7 / 58 oC5emu2NegK
    0 Q60T + mAlW70nkMtlMSOFChQ8w72hFLnm + TEALW4ITyih3jFH5IZFAOi1MtuaYHK
    oVgYLqNN3fQ++ygDAIs965fSqTBiSg1GwLoozskOvD4XCupL6S3JxxrM4lspHAtv
    KQIDAQAB
    -- -- - END PUBLIC KEY-- -- -
    "
}
```

The PCI-DSS rules implies that every client or server APIs that use directly or indirectly our payment gateway, SHALL never send the credit card data in their raw form to our servers (including RAM due to a form post). If not, then the PCI-DSS applies to the implementer with all it involves (PCI data standards covers network security, operating system patches, code quality and liability and so on).

### HTTP Request

`GET https://my.appstore.com/api/payment/token/get`

### Auth Required

`YES`

### Response Parameters

Parameter | Type | Description
--------- | ---- | -----------
token | string | Encryption token (to be passed to the purchase API when using cc).
publicKey | string | RSA public key to be used for cc data encryption (details below).

## Purchase an item

> Pay with an existing agreement (saved method)

```json
{
    "sku": "com.sample.myapp",
    "agreementId": "b7ed35d2-b72f-11e2-91b1-de50000001ff"
}
```

> Pay with an existing agreement (saved method) + Password verification

```json
{
    "sku": "com.sample.myapp",
    "agreementId": "b7ed35d2-b72f-11e2-91b1-de50000001ff",
    "password": "mypassword"
}
```

> Pay with customer credit (piggy bank)

<aside class="warning">When you want to purchase an item using the customer credit, balance must be positive.</aside>

```json
{
    "sku": "com.sample.myapp",
    "useCredit": true
}
```

> Pay with a credit card (initial purchase)

```json
{
    "sku": "com.sample.myapp",
    "paymentDetails": {
        "paymentMethod": "WorldPay/visa",
        "ccEncryptedData": "yP7dHxEid8DYrjrOafmk7Tbz69LuiPemL+GdKo6KeBaOuyNKj1Z5gJy4/ktrckITATZEzBgnf3Cb
        NIFyxqMdfQF + H5keuX29Yyqax1wwjyXvjObD2yZUIF3l4BargE9xPRmEeA3qpWP + ddjDd9njVgbU
        Qd / UtvjNfBqnaUVj90ZZ2RtB6wFytvGcxIo0ovuUeKfaJiB4T2trFmH6nHaz1NImz80jkLXbbYYU
        f6Xa7AlUDL9UKMLnmtB5gYwt0EBxMqVviD / zKK3 + xioZWCPU5RXm / 5 oNuTWsWqa64KVHP0q83J70
        zwmwerrUmUGLLSzz1UNIOK9m4w88op3R / qgKtg == "
        ",
        "ccEncryptionToken": "a9488248-2dc9-4cfd-b048-26b5c316c431"
    }
}
```

> Pay with a credit card (initial purchase + saving the method in the wallet)

```json
{
    "sku": "com.sample.myapp",
    "paymentDetails": {
        "paymentMethod": "WorldPay/visa",
        "ccEncryptedData": "yP7dHxEid8DYrjrOafmk7Tbz69LuiPemL+GdKo6KeBaOuyNKj1Z5gJy4/ktrckITATZEzBgnf3Cb
        NIFyxqMdfQF + H5keuX29Yyqax1wwjyXvjObD2yZUIF3l4BargE9xPRmEeA3qpWP + ddjDd9njVgbU
        Qd / UtvjNfBqnaUVj90ZZ2RtB6wFytvGcxIo0ovuUeKfaJiB4T2trFmH6nHaz1NImz80jkLXbbYYU
        f6Xa7AlUDL9UKMLnmtB5gYwt0EBxMqVviD / zKK3 + xioZWCPU5RXm / 5 oNuTWsWqa64KVHP0q83J70
        zwmwerrUmUGLLSzz1UNIOK9m4w88op3R / qgKtg == "
        ",
        "ccEncryptionToken": "a9488248-2dc9-4cfd-b048-26b5c316c431"
    }
}
```

> Response example

```json
{
    "response": {
        "success": true,
        "message": ""
    },
    "orderId": "432157674",
    "orderDate": "20130610 12:02:35"
}
```

This endpoint handles purchases.  

### HTTP Request

`GET https://my.appstore.com/api/payment/token/get`

### Auth Required

`YES`

### JSON Request Parameters

Parameter | Mandatory | Default | Description
--------- | --------- | ------- | -----------
sku | yes | none | The item or application.
useCredit | yes | true | To pay using internal credit balance.
agreementId | no | none | The wallet agreementId. If blank the paymentDetails node must be set.
password | no | none | User's store password (password is checked only when using agreementId).
paymentDetails.paymentMethod | no | none | Payment method to use (returned by the wallet in "paymentMethods" array).
paymentDetails.ccEncryptionToken | no | none | The credit card encryption token.
paymentDetails.ccEncryptedData | no | none | The credit card holder data (encrypted with the RSA public key) see below for details.
paymentDetails.addToWallet | no | none | If true the credit card (or an other compatible method) will be added in the wallet.
paymentDetails.ccIssuerId | no | none | Encryption token (to be passed to the purchase API when using cc). If addToWallet is enabled, and if method is a credit card this field is required, first 6 digits of the card.
paymentDetails.ccExpirationDate | no | none | Encryption token (to be passed to the purchase API when using cc). If addToWallet is enabled, and if method is a credit card this field is required, (MM/YYYY).

### Response Parameters

Parameter | Type | Description
--------- | ---- | -----------
success | boolean | If the purchase went well or not.
message | string | A message which explains if an error occurred.
status | string | With possible statuses: `complete`, `processing`, `fraud`.
orderId | string | Unique Order identifier
orderDate | string | Transaction date.

### Possible errors

Code | Meaning
---- | -------
7000 | Invalid Agreement ID
7001 | Missing either `agreementId`, `paymentDetails` or `useCredit` parameter
7002 | Invalid SKU
7003 | No Billing Address found
7005 | Unknown payment method
7006 | Payment unavailable
7007 | Unavailable payment method
7008 | Cannot decrypt request with the given encryption key/data
7009 | Invalid password
7010 | Payment declined `%s`
7011 | Multiple payment methods passed (Please pass only one)
7012 | Empty balance
7013 | Cannot fulfill credit balance with credit method
7023 | Credit balance is too low to complete purchase
7999 | Unhandled error `%s`