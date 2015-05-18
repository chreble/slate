
# Featured

## Get a specific Page

> Response example

```json
{
    "id": "8",
    "name": "Accueil",
    "key": "acer-home",
    "options": {
        "pageSubtitle": "Bienvenue sur l'appstore Acer !"
    },
    "blocks": [{
        "id": "28",
        "name": "Top Jeux action",
        "key": "top-jeux-action",
        "representation": "highlights",
        "options": {
            "quantityLimit": 5,
            "showMore": true,
            "showMoreLimit": 20
        },
        "products": [{
            "type": "app",
            "sku": "com.cravecreative.eastereggjump",
            "name": "Easter Egg Jump",
            "priceFormatted": "\u20ac0.99",
            "price": 0.9899635446,
            "rating": 0,
            "nbReviews": 0,
            "publisherName": "Crave Creative",
            "shortDescription": "Guide the baby chick over the Easter eggs to boost him upward.\r\n",
            "imageCarousel": "http:\/\/cdn.mobile.nexway.com\/media\/catalog\/product\/e\/a\/easter-egg-jump-1024x500.png",
            "icon": "http:\/\/cdn.mobile.nexway.com\/media\/catalog\/product\/e\/a\/easter-egg-jump-icon-512.png"
        }, {
            "type": "app",
            "sku": "org.jymc.spacegame.FeedTheFishy",
            "name": "Feed The Fishy",
            "priceFormatted": "\u20ac0.91",
            "price": 0.91304631,
            "rating": 0,
            "nbReviews": 0,
            "publisherName": "Mobile Streams",
            "shortDescription": "This a very addictive game, the whole purpose is to help the fishy swim from one point to the other. Energy gets reduced, so you need to eat smaller fishes and other items to boost your energy level.",
            "imageCarousel": "http:\/\/cdn.mobile.nexway.com\/media\/catalog\/product\/t\/i\/title_1_30.png",
            "icon": "http:\/\/cdn.mobile.nexway.com\/media\/catalog\/product\/i\/c\/icon_30_1_12.png"
        }]
    }]
}
```

This endpoint retrieves the given page and the blocks it contains.  
Using pages instead of blocks is very powerful since it allows to reorganise the whole content through Nexway's admin panel.

### HTTP Request

`GET https://my.appstore.com/api/catalog/featured/page/key/appstore-page/storeId/11/age/0-3`

### Query Parameters

Parameter | Mandatory | Default | Description
--------- | --------- | ------- | -----------
storeId | yes | none | The storeId defines many things, such as the currency, the language, the availability.
key | no | none | The featured page key.
id  | no | none | The featured page id (this one has priority over `key` parameter if passed).
age | no | all | If you want to filter the output by age range (ex. `0-3`, `3-`)
compatibility | no | all | If you want to filter the output by device screen compatibility. Must be specified as: `4` = 4-inch, `7` = 7-inch, `10` = 10-inch (comma separated).

## Get a specific Block

> Response example

```json
{
    "id": "28",
    "name": "Top Jeux action",
    "key": "top-jeux-action",
    "representation": "highlights",
    "options": {
        "quantityLimit": 5,
        "showMore": true,
        "showMoreLimit": 20
    },
    "products": [{
        "type": "app",
        "sku": "com.cravecreative.eastereggjump",
        "name": "Easter Egg Jump",
        "priceFormatted": "\u20ac0.99",
        "price": 0.9899635446,
        "rating": 0,
        "nbReviews": 0,
        "publisherName": "Crave Creative",
        "shortDescription": "Guide the baby chick over the Easter eggs to boost him upward.\r\n",
        "imageCarousel": "http:\/\/cdn.mobile.nexway.com\/media\/catalog\/product\/e\/a\/easter-egg-jump-1024x500.png",
        "icon": "http:\/\/cdn.mobile.nexway.com\/media\/catalog\/product\/e\/a\/easter-egg-jump-icon-512.png"
    }, {
        "type": "app",
        "sku": "org.jymc.spacegame.FeedTheFishy",
        "name": "Feed The Fishy",
        "priceFormatted": "\u20ac0.91",
        "price": 0.91304631,
        "rating": 0,
        "nbReviews": 0,
        "publisherName": "Mobile Streams",
        "shortDescription": "This a very addictive game, the whole purpose is to help the fishy swim from one point to the other. Energy gets reduced, so you need to eat smaller fishes and other items to boost your energy level.",
        "imageCarousel": "http:\/\/cdn.mobile.nexway.com\/media\/catalog\/product\/t\/i\/title_1_30.png",
        "icon": "http:\/\/cdn.mobile.nexway.com\/media\/catalog\/product\/i\/c\/icon_30_1_12.png"
    }]
}
```

This endpoint retrieves a specific block and the products associated to it.

### HTTP Request

`GET https://my.appstore.com/api/catalog/featured/block/key/appstore-block/storeId/11/age/0-3`

### Query Parameters

Parameter | Mandatory | Default | Description
--------- | --------- | ------- | -----------
storeId | yes | none | The storeId defines many things, such as the currency, the language, the availability.
key | yes | none | The featured block key.
id  | no | none | The featured block id (this one has priority over `key` parameter if passed).
age | no | all | If you want to filter the output by age range (ex. `0-3`, `3-`)
compatibility | no | all | If you want to filter the output by device screen compatibility. Must be specified as: `4` = 4-inch, `7` = 7-inch, `10` = 10-inch (comma separated).


## Get all products of a given block

> Response example

```json
{
    "id": "28",
    "name": "Top Jeux action",
    "key": "top-jeux-action",
    "products": [{
        "type": "app",
        "sku": "com.cravecreative.eastereggjump",
        "name": "Easter Egg Jump",
        "priceFormatted": "€0.99",
        "price": 0.9899635446,
        "rating": 0,
        "nbReviews": 0,
        "publisherName": "Crave Creative",
        "shortDescription": "Guide the baby chick over the Easter eggs to boost him upward.",
        "imageCarousel": "http://cdn.mobile.nexway.com/media/catalog/product/e/a/easter-egg-jump-1024x500.png",
        "icon": "http://cdn.mobile.nexway.com/media/catalog/product/e/a/easter-egg-jump-icon-512.png"
    }]
}
```

This endpoint retrieves all products associated to a block (with a hard limit of 200 products), it works in combination with the `highlights` representation, `block` and `page` requests being constrained with lesser quantity limits.

### HTTP Request

`GET https://my.appstore.com/api/catalog/featured/products/blockId/28/storeId/11/age/0-3`

### Query Parameters

Parameter | Mandatory | Default | Description
--------- | --------- | ------- | -----------
storeId | yes | none | The storeId defines many things, such as the currency, the language, the availability.
blockId | yes | none | The featured block id.
age | no | all | If you want to filter the output by age range (ex. `0-3`, `3-`)
compatibility | no | all | If you want to filter the output by device screen compatibility. Must be specified as: `4` = 4-inch, `7` = 7-inch, `10` = 10-inch (comma separated).
