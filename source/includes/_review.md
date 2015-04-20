# Review

## Get a list of reviews

```shell
curl -X GET "https://my.appstore.com/api/review/list/sku/com.magmamobile.game.IceCream" \
    -H "Authorization: XXX"
```

> The above command returns JSON structured like this:

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
sku | yes | none | The application SKU.
nbItems | no | 10 | If you want to filter the output by device screen compatibility.
page | no | 1 | If you want to filter the output by device screen compatibility.

## Submit a review

```shell
curl -X POST "https://my.appstore.com/api/review/submit" \
    -H "Authorization: XXX" \
    -H "Content-Type: application/json" \
    -d "{\"sku\":\"com.example.app\",\"rating\":1.5,\"title\":\"Title of the review\",\"detail\":\"Your product is just amazing\",\"nickname\":\"Anonymous Guy\"}"
```

> The above command returns JSON structured like this:

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

### JSON Parameters

Parameter | Mandatory | Default | Description
--------- | --------- | ------- | -----------
sku | yes | none | The application SKU.
rating | yes | none | From 1 to 5.
title | yes | none | The review title.
detail | yes | none | The review description.
nickname | yes | none | The user nickname.