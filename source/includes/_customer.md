# Customer

## Get a list of reviews

```shell
curl -XGET "https://my.appstore.com/api/review/list/sku/com.magmamobile.game.IceCream"
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
curl -XPOST "https://my.appstore.com/api/locale/region/list/countryId/FR"
```

> The above command returns JSON structured like this:

```json
{
    "regions": [{
        "region": "182",
        "name": "Ain"
    }, {
        "region": "183",
        "name": "Aisne"
    }]
}
```

This endpoint retrieves a list of regions available on the given country.

### HTTP Request

`GET https://my.appstore.com/api/locale/region/list/countryId/FR`

### Auth Required

`YES`

### Query Parameters

Parameter | Mandatory | Default | Description
--------- | --------- | ------- | -----------
countryId | yes | none | The country formatted in two letters, ex. FR, PL.
