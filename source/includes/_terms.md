# Terms and conditions

## Get the terms and conditions

> Response example

```json
{
    "success": true,
    "checkboxText": "I accept the terms and conditions",
    "content": "<b>Chapter 1</b>asdasdasdasda asdasd asd asd asd asdads asd asd asdasdasd teythrr ertert."
}
```

The Terms and Conditions API provides a bridge to Magento's Terms and conditions manager (under Sales).

### HTTP Request

`GET https://my.appstore.com/api/terms/index`

### Auth Required

`YES`

### Query Parameters

Parameter | Mandatory | Default | Description
--------- | --------- | ------- | -----------
storeId | yes | none | The storeId defines many things, such as the currency, the language, the availability.

### Response Parameters

Parameter | Type | Description
--------- | ---- | -----------
success | boolean | If the purchase went well or not.
checkboxText | string | Acceptation text ex. "I accept the Terms and conditions".
content | string (html) | Terms and conditions.