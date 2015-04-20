# Home

## Get home categories

```shell
curl -X GET "https://my.appstore.com/api/catalog/category/home/storeId/11"
```

> The above command returns JSON structured like this:

```json
{
    "carousel": [{
        "sku": "sk.inlogic.protennis2015",
        "image": "https://kurio.appstore.dev/media/catalog/product/t/e/tenis_profesional_2015.jpg"
    }, {
        "sku": "sk.inlogic.superpocketfootball2014",
        "image": "https://kurio.appstore.dev/media/catalog/product/s/_/s_per_bolsillo_de_f_tbol_2014.jpg"
    }],
    "categoriesMenu": [{
        "categoryId": 144,
        "name": "ALLE",
        "icon": "all"
    }, {
        "categoryId": 150,
        "name": "Free",
        "icon": "free"
    }],
    "categoriesBody": [{
        "categoryId": 143,
        "name": "Ny",
        "nbApps": 19,
        "apps": [{
            "sku": "com.thumbstar.spaceoff",
            "name": "Space Off",
            "image": "https://kurio.appstore.dev/media/catalog/product/s/p/spaceoffstorelogo512x512.png",
            "price": 15.7149305,
            "priceFormatted": "15,71 krN",
            "publisherName": "Thumbstar",
            "rating": 0,
            "nbReviews": 0,
            "gameRating": {
                "age": "3"
            }
        }, {
            "sku": "com.thumbstar.tinyphonepeople",
            "name": "Tiny Phone People",
            "image": "https://kurio.appstore.dev/media/catalog/product/i/c/icon_4.png",
            "price": 15.7149305,
            "priceFormatted": "15,71 krN",
            "publisherName": "Thumbstar",
            "rating": 0,
            "nbReviews": 0,
            "gameRating": {
                "age": "3"
            }
        }]
    }, {
        "categoryId": 142,
        "name": "Toppselgere",
        "nbApps": 20,
        "apps": [{
            "sku": "com.outfit7.talkinggingerfree",
            "name": "Talking Ginger",
            "image": "https://kurio.appstore.dev/media/catalog/product/i/c/icon-r-114.png",
            "price": 0,
            "priceFormatted": "free",
            "publisherName": "Outfit 7",
            "rating": 0,
            "nbReviews": 0,
            "gameRating": {
                "age": "3"
            }
        }]
    }]
}
```

This endpoint retrieves all categories and their applications for the Home screen.

### HTTP Request

`GET https://my.appstore.com/api/catalog/category/home/storeId/11`

### Query Parameters

Parameter | Mandatory | Default | Description
--------- | --------- | ------- | -----------
storeId | yes | none | The storeId defines many things, such as the currency, the language, the availability.
categoryId | yes | none | The category identifier.
age | no | all | If you want to filter the output by age range (ex. `0-3`, `3-`)
compatibility | no | all | If you want to filter the output by device screen compatibility. Must be specified as: `4` = 4-inch, `7` = 7-inch, `10` = 10-inch (comma separated).
nbItems | no | 10 | If you want to filter the output by device screen compatibility.

<aside class="warning">The `age` filter doesn't work, see (#110)[https://github.com/NexwayGroup/N3-AppStore/issues/110].</aside>