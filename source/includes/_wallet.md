# Wallet

## Notes on encryption

The PCI-DSS rules implies that every client or server APIs that use directly or indirectly our payment gateway, SHALL never send the credit card data in their raw form to our servers (including RAM due to a form post). If not, then the PCI-DSS applies to the implementer with all it involves (PCI data standards covers network security, operating system patches, code quality and liability and so on).

### How-To

You have to generate a query string with the following parameters:

Required
- ccNumber : (string) Credit card number (19 digits max)
- ccExpirationMonth : (string) Month representation on two digits (use zerofill ex: "09").
- ccExpirationYear : (string) Year representation on four digits (ex: "2015").
- ccCvv: (string) Card verification value (4 digits max)

Not required
- ccIssueNumber: (string) Card issue number - Ask only for MAESTRO card (2 digits max)
- ccStartDate: (string) Card start date - Ask only for MAESTRO card (MM/YYYY)
Ex: `ccNumber=4111111111111111&ccExpirationMonth=12&ccExpirationYear=2015&ccCvv=000`
Base64 encode the result
Encrypt the base64 encoded string using the RSA public key
Base64 encode the binary result and pass it to ccEncryptedData.

Example (in Java using BouncyCastle)

```java
key = key.replaceAll("-----BEGIN PUBLIC KEY-----", "");
key = key.replaceAll("-----END PUBLIC KEY-----", "");

Security.addProvider(new org.bouncycastle.jce.provider.BouncyCastleProvider());
BASE64Encoder b64e = new BASE64Encoder();
BASE64Decoder b64d = new BASE64Decoder();
AsymmetricKeyParameter publicKey = 
    (AsymmetricKeyParameter) PublicKeyFactory.createKey(b64d.decodeBuffer(key));

AsymmetricBlockCipher e = new RSAEngine();
e = new org.bouncycastle.crypto.encodings.PKCS1Encoding(e);
e.init(true, publicKey);

String result = b64e.encode(input.getBytes());

byte[] messageBytes = b64e.encode(input.getBytes()).getBytes();
System.out.println(result);
byte[] hexEncodedCipher = e.processBlock(messageBytes, 0, messageBytes.length);

String output = b64e.encode(hexEncodedCipher);
```

Example (using PHP)

```php
<?php
$data = base64_encode(http_build_query($data));

openssl_public_encrypt($data, $encrypted, $encryptionKey);
$ccEncryptedData = base64_encode($encrypted);
?>
```

## Get the available payment methods

```shell
curl -X GET "https://my.appstore.com/api/payment/wallet/list" \
    -H "Authorization: XXX"
```

> The above command returns JSON structured like this:

```json
{
    "agreements": [{
        "agreementId": "b2dba034-ce06-4560-81eb-9e0150a8767e",
        "agreementLabel": "Visa",
        "isCreditCard": true,
        "ccType": "visa",
        "ccBin": "414720**********",
        "ccExpirationDate": "11/2017"
    }],
    "methods": [{
        "isCreditCard": true,
        "label": "Visa",
        "key": "visa",
        "id": "Atos/visa",
        "canSaveToWallet": true
    }, {
        "isCreditCard": true,
        "label": "American Express",
        "key": "amex",
        "id": "Atos/amex",
        "canSaveToWallet": true
    }],
    "credit": {
        "label": "Customer Credit",
        "balance": 0,
        "balanceFormatted": "0,00 €",
        "balanceCurrency": "EUR",
        "enabled": false
    }
}
```

This endpoint retrieves the agreements (saved methods) as well as available methods for payment.  
The response may differ depending of the customer type.

### HTTP Request

`GET https://my.appstore.com/api/payment/wallet/list`

### Auth Required

`YES`

## Add a new agreement in the wallet

```shell
curl -X POST "https://my.appstore.com/api/payment/wallet/add" \
    -H "Authorization: XXX" \
    -H "Content-Type: application/json" \
    -d "{\"paymentDetails\":{\"paymentMethod\":\"WorldPay/visa\",\"ccEncryptedData\": \"yP7dHxEid8DYrjrOafmk7Tbz69LuiPemL+GdKo6KeBaOuyNKj1Z5gJy4/ktrckITATZEzBgnf3....\",\"ccEncryptionToken\": \"a9488248-2dc9-4cfd-b048-26b5c316c431\",\"ccIssuerId\":\"511237\",\"ccExpirationDate\":\"11/2014\",\"isDefault\":true}}"
```

> The above command returns JSON structured like this:

```json
{
    "success": true,
    "billingAgreementId": "1de769eb-961f-490f-92dc-f172e272330a"
}
```

This endpoint adds a new agreement (saved payment method) in the wallet.

<aside class="notice">When you want to pass credit card data to the API you have to use encryption.</aside>

### HTTP Request

`POST https://my.appstore.com/api/payment/wallet/add`

### Auth Required

`YES`

### JSON Parameters

Parameter | Mandatory | Default | Description
--------- | --------- | ------- | -----------
paymentMethod | yes | none | The payment method name.
ccEncryptedData | yes | none | The credit card encrypted data.
ccEncryptionToken | yes | none | The encryption token.
ccIssuerId | yes | none | The credit card issuer ID.
ccExpirationDate | yes | none | The credit card expiration date.
isDefault | yes | 0 | The user nickname.

## Delete an agreement from the wallet

```shell
curl -X POST "https://my.appstore.com/api/payment/wallet/delete" \
    -H "Authorization: XXX" \
    -H "Content-Type: application/json" \
    -d "{\"billingAgreementId\":\"1de769eb-961f-490f-92dc-f172e272330a\"}"
```

> The above command returns JSON structured like this:

```json
{
    "success": true,
    "billingAgreementId": "1de769eb-961f-490f-92dc-f172e272330a"
}
```

This endpoint deletes an agreement (saved payment method) from the wallet.

### HTTP Request

`POST https://my.appstore.com/api/payment/wallet/delete`

### Auth Required

`YES`
