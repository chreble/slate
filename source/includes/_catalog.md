# Catalog

## Get a list of categories

```shell
curl "https://my.appstore.com/api/catalog/category/list/storeId/11"
```

> The above command returns JSON structured like this:

```json
{
    "categories": {
        "3": {
            "categoryId": 3,
            "name": "Bøker & Tegneserier",
            "subCats": {
                "5": {
                    "categoryId": 5,
                    "name": "Childrens Books"
                }
            }
        },
        "15": {
            "categoryId": 15,
            "name": "Utdanning",
            "subCats": {
                "16": {
                    "categoryId": 16,
                    "name": "Historikk"
                },
                "17": {
                    "categoryId": 17,
                    "name": "Language (Spoken)",
                    "subCats": {
                        "149": {
                            "categoryId": 149,
                            "name": "Spanish"
                        }
                    }
                }
            }
        }
    }
}
```

This endpoint retrieves the list of categories available for the given `storeId`.  

### HTTP Request

`GET https://my.appstore.com/api/catalog/category/list/storeId/11`

### Query Parameters

Parameter | Mandatory | Default | Description
--------- | --------- | ------- | -----------
storeId | yes | none | The storeId defines many things, such as the currency, the language, the availability.

## Get applications inside category

```shell
curl "https://my.appstore.com/api/catalog/category/index/categoryId/15/storeId/11"
```

> The above command returns JSON structured like this:

```json
{
    "apps": [{
        "sku": "com.thup.lunchbox",
        "name": " Monkey Preschool Lunchbox",
        "priceFormatted": "15,71 krN",
        "price": 15.7149305,
        "image": "https://kurio.appstore.dev/media/catalog/product/m/p/mpl_icon_114.png",
        "rating": 0,
        "nbReviews": 0,
        "publisherName": "THUP",
        "versionCode": 20,
        "versionLabel": "2.0",
        "gameRating": {
            "age": "3"
        }
    }, {
        "sku": "com.marbotic.ipad.dixdoigts",
        "name": "10 fingers +",
        "priceFormatted": "15,71 krN",
        "price": 15.7149305,
        "image": "https://kurio.appstore.dev/media/catalog/product/i/c/icon_20_11.png",
        "rating": 0,
        "nbReviews": 0,
        "publisherName": "Marbotic",
        "versionCode": 6,
        "versionLabel": "3.0.3"
    }],
    "nbApps": 175,
    "subCats": [{
        "categoryId": "68",
        "name": "Alfabetet"
    }, {
        "categoryId": "69",
        "name": "Dyr"
    }]
}
```

This endpoint retrieves applications attached to a given category.

### HTTP Request

`GET https://my.appstore.com/api/catalog/category/index/categoryId/15/storeId/11`

### Query Parameters

Parameter | Mandatory | Default | Description
--------- | --------- | ------- | -----------
storeId | yes | none | The storeId defines many things, such as the currency, the language, the availability.
categoryId | yes | none | The category identifier.
age | no | all | If you want to filter the output by age range (ex. `0-3`, `3-`)
compatibility | no | all | If you want to filter the output by device screen compatibility. Must be specified as: `4` = 4-inch, `7` = 7-inch, `10` = 10-inch (comma separated).
nbItems | no | 20 | If you want to filter the output by device screen compatibility.
page | no | 1 | If you want to filter the output by device screen compatibility.

## Get home categories

```shell
curl "https://my.appstore.com/api/catalog/category/home/storeId/11"
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

<aside class="warning">The `age` filter doesn't work, see [#110](https://github.com/NexwayGroup/N3-AppStore/issues/110).</aside>

## Get application information

```shell
curl "https://my.appstore.com/api/catalog/product/app/sku/com.pepworks.ocean_memo_game/storeId/11"
```

> The above command returns JSON structured like this:

```json
{
    "id": "2602",
    "sku": "com.pepworks.ocean_memo_game",
    "name": "Card pairs puzzle ocean animal",
    "description": "Description\r\nThis is the perfect animal puzzle app to have a good time with your children!\r\nYour kids will just love these amazing hand-drawn animal-pictures while playing and training it's memory!\r\nThis fun matching game helps improve visual perception & develop fine motor skills by finding pairs of animal pictures. It gives positive and pleasant feedback for the child. Trains your kids brain with this pairs game and improve skills like:\r\nShape recognition, logical thinking, tactile and cognitive skills, problem solving, concentration and memory.\r\nGAME PLAY:\r\nChoose your level of difficulty by touching one of the card sets. Now start to train your memory -\r\nMatch pairs of ocean animal cards:\r\nThe game starts with all memory cards turned face down. Tap on one of the memory card and remember the picture on it. With the next tap try to find and flip the memory card with the same picture as previous one. If the pictures on the both memory cards will be the same they will stay opened and you can continue to search for the next pairs. Otherwise both cards will flip back over and you will get another try to match cards.\r\nGAME FEATURES:\r\n- Brain activity educational game for kids for preschoolers, toddlers and their parents\r\n- Different levels of difficulty, from 4 to 14 pieces\r\n- Endless replay possibility\r\n- Colorful images to be easily remembered\r\n- HD graphic designed for toddlers and preschoolers\r\n- Designed for both - mobiles and tablets\r\n- Nice sound effects and soundtrack\r\n- Visual memory & short term memory training\r\n- Concentration & cognition skills improvement",
    "priceFormatted": "15,71 krN",
    "price": 15.7149305,
    "currency": "NOK",
    "packageName": "com.pepworks.ocean_memo_game",
    "apk": "http://cdn.mobile.nexway.com/com.pepworks.ocean_memo_game-1-enc.apk",
    "ageMin": "3",
    "apkEncrypted": true,
    "apkHashMac": "b0eeceeb02bac48f3ad6bb91bba3981a538477c9",
    "version": "1",
    "publisherName": "Pepworks",
    "rating": 0,
    "versionCode": 1,
    "versionLabel": "1.0",
    "medias": {
        "image": "https://kurio.appstore.dev/media/catalog/product/i/c/icon_31_4.png",
        "screenshots": [],
        "videos": []
    },
    "permissions": [
        "Permet d'utiliser le gestionnaire d'énergie afin d'empêcher l'appareil de se mettre en veille (processeur, écran)."
    ],
    "changelog": null,
    "reviews": [],
    "nbReviews": 0
}
```

This endpoint retrieves the detailed information about a specific application.

### HTTP Request

`GET https://my.appstore.com/api/catalog/product/app/sku/com.pepworks.ocean_memo_game/storeId/11`

### Query Parameters

Parameter | Mandatory | Default | Description
--------- | --------- | ------- | -----------
storeId | yes | none | The storeId defines many things, such as the currency, the language, the availability.
sku | yes | none | The application SKU.

## Get in-app item information

```shell
curl "https://my.appstore.com/api/catalog/product/item/sku/com.pepworks.ocean_memo_game/storeId/11"
```

> The above command returns JSON structured like this:

```json
{
    "appName": "My Wonderful App !",
    "editorName": "My Company TM",
    "appIcon": "http://cdn.mobile.nexway.com/apps/com.mywonderfullapp/logo.png",
    "items": [{
        "sku": "itemsku1",
        "reference": "1",
        "priceFormatted": "3,4 €",
        "price": 3.4,
        "currency": "EUR",
        "name": "First Item",
        "description": "bla bla",
        "purchased": true
    }, {
        "sku": "itemsku2",
        "reference": "2",
        "priceFormatted": "2,99 €",
        "price": 2.99,
        "currency": "EUR",
        "name": "First Item",
        "description": "bla bla",
        "consumable": true
    }]
}
```

This endpoint retrieves the detailed information about an in-app item.

### HTTP Request

`GET https://my.appstore.com/api/catalog/product/item/sku/com.pepworks.ocean_memo_game/storeId/11`

### Query Parameters

Parameter | Mandatory | Default | Description
--------- | --------- | ------- | -----------
storeId | yes | none | The storeId defines many things, such as the currency, the language, the availability.
sku | yes | none | The in-app item SKU.

## Get latest version of app/item

```shell
curl "https://my.appstore.com/api/catalog/product/version/index/skus/com.pepworks.ocean_memo_game/storeId/11"
```

> The above command returns JSON structured like this:

```json
[{
    "sku": "com.pepworks.ocean_memo_game",
    "versionCode": 1,
    "versionLabel": "1.0"
}]
```

This endpoint retrieves the latest version of the given app(s)/item(s).

<aside class="notice">This endpoint is particulary helpful if you need to compare the installed version to the latest one available.</aside>

### HTTP Request

`GET https://my.appstore.com/api/catalog/product/version/index/skus/com.pepworks.ocean_memo_game`

### Query Parameters

Parameter | Mandatory | Default | Description
--------- | --------- | ------- | -----------
skus | yes | none | A list of comma-separated skus.

## Search Application

```shell
curl "https://my.appstore.com/api/catalog/search/index/search/ginger/storeId/11"
```

> The above command returns JSON structured like this:

```json
{
    "apps": [{
        "sku": "com.outfit7.talkinggingerfree",
        "name": "Talking Ginger",
        "priceFormatted": "free",
        "price": 0,
        "image": "https://kurio.appstore.dev/media/catalog/product/i/c/icon-r-114.png",
        "rating": 0,
        "nbReviews": 0,
        "publisherName": "Outfit 7",
        "versionCode": 53,
        "versionLabel": "1.5.1",
        "gameRating": {
            "age": "3"
        }
    }, {
        "sku": "com.advancedmobilesolutions.candypro",
        "name": "Candy Blast",
        "priceFormatted": "7,82 krN",
        "price": 7.8179805,
        "image": "https://kurio.appstore.dev/media/catalog/product/c/a/candy_icon_512.png",
        "rating": 0,
        "nbReviews": 0,
        "publisherName": "SoAppy",
        "versionCode": 2,
        "versionLabel": "2.0",
        "gameRating": {
            "age": "3"
        }
    }]
}
```

This endpoint shows paginated search results which matches the given search string.

<aside class="notice">This endpoint is particulary helpful if you need to compare the installed version to the latest one available.</aside>

### HTTP Request

`GET https://my.appstore.com/api/catalog/search/index/search/ginger/storeId/11`

### Query Parameters

Parameter | Mandatory | Default | Description
--------- | --------- | ------- | -----------
storeId | yes | none | The storeId defines many things, such as the currency, the language, the availability.
search | yes | none | The search query.
age | no | all | If you want to filter the output by age range (ex. `0-3`, `3-`)
compatibility | no | all | If you want to filter the output by device screen compatibility. Must be specified as: `4` = 4-inch, `7` = 7-inch, `10` = 10-inch (comma separated).
nbItems | no | 20 | If you want to filter the output by device screen compatibility.
page | no | 1 | If you want to filter the output by device screen compatibility.