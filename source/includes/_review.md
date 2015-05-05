# Review

## Get a list of reviews

> Response example

```json
{
    "reviews": [{
        "title": "love",
        "detail": "it flickers sometimes\nI love this game",
        "nickname": "Kaylee",
        "createdAt": "27/01/2015",
        "rating": 0
    }, {
        "title": "awsome ",
        "detail": "its so much fun and its totally FREE",
        "nickname": "Liz Valenzuela",
        "createdAt": "27/01/2015",
        "rating": 0
    }]
}
```

This endpoint retrieves a list of reviews for the given product.  

### HTTP Request

`GET https://my.appstore.com/api/review/list/sku/com.magmamobile.game.IceCream`

### Auth Required

`YES`

### Query Parameters

Parameter | Mandatory | Default | Description
--------- | --------- | ------- | -----------
storeId | yes | none | The store ID.
sku | yes | none | The application SKU.
nbItems | no | 10 | If you want to filter the output by device screen compatibility.
page | no | 1 | If you want to filter the output by device screen compatibility.

## Submit a review

> Response example

```json
{
  "success": true
}
```

This endpoint submits a review for the given product.

<aside class="notice">The review must be manually approved in the AppStore admin panel.</aside>

### HTTP Request

`POST https://my.appstore.com/api/review/submit`

### Auth Required

`YES`

### JSON Request Parameters

Parameter | Mandatory | Default | Description
--------- | --------- | ------- | -----------
storeId | yes | none | The store ID.
sku | yes | none | The application SKU.
rating | yes | none | From 1 to 5.
title | yes | none | The review title.
detail | yes | none | The review description.
nickname | yes | none | The user nickname.
