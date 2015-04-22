
# Featured

## Get a specific Page

> Response example

```json
{
    "id":"8",
    "name":"Accueil",
    "key":"acer-home",
    "options":{
        "pageSubtitle":"Bienvenue sur l'appstore Acer !"
    },
    "blocks":[
        {
            "id":"28",
            "name":"Top Jeux action",
            "key":"top-jeux-action",
            "representation":"highlights",
            "options":{
                "quantityLimit":5,
                "showMore":true,
                "showMoreLimit":20
            },
            "products":[
                {
                    "type":"app",
                    "sku":"com.cravecreative.eastereggjump",
                    "name":"Easter Egg Jump",
                    "priceFormatted":"\u20ac0.99",
                    "price":0.9899635446,
                    "rating":0,
                    "nbReviews":0,
                    "publisherName":"Crave Creative",
                    "shortDescription":"Guide the baby chick over the Easter eggs to boost him upward.\r\n",
                    "imageCarousel":"http:\/\/cdn.mobile.nexway.com\/media\/catalog\/product\/e\/a\/easter-egg-jump-1024x500.png",
                    "icon":"http:\/\/cdn.mobile.nexway.com\/media\/catalog\/product\/e\/a\/easter-egg-jump-icon-512.png"
                },
                {
                    "type":"app",
                    "sku":"org.jymc.spacegame.FeedTheFishy",
                    "name":"Feed The Fishy",
                    "priceFormatted":"\u20ac0.91",
                    "price":0.91304631,
                    "rating":0,
                    "nbReviews":0,
                    "publisherName":"Mobile Streams",
                    "shortDescription":"This a very addictive game, the whole purpose is to help the fishy swim from one point to the other. Energy gets reduced, so you need to eat smaller fishes and other items to boost your energy level.",
                    "imageCarousel":"http:\/\/cdn.mobile.nexway.com\/media\/catalog\/product\/t\/i\/title_1_30.png",
                    "icon":"http:\/\/cdn.mobile.nexway.com\/media\/catalog\/product\/i\/c\/icon_30_1_12.png"
                },
                {
                    "type":"app",
                    "sku":"com.jarbull.streetball",
                    "name":"Streetball Shootout",
                    "priceFormatted":"\u20ac0.91",
                    "price":0.91304631,
                    "rating":0,
                    "nbReviews":0,
                    "publisherName":"Spoiled Milk Limited",
                    "shortDescription":"Hit the streets instantly and test your basketball skills on the urban courts in STREETBALL SHOOTOUT! Try to score as many shots as you can without missing and try to be the streetball master.",
                    "icon":"http:\/\/cdn.mobile.nexway.com\/media\/catalog\/product\/c\/o\/collateral_action_1_productCode_10667_id_15_w_110_h_110_name_wap-110x110_3.jpg"
                },
                {
                    "type":"app",
                    "sku":"com.dotemu.rtype",
                    "name":"R-TYPE",
                    "priceFormatted":"\u20ac1.79",
                    "price":1.7900319021,
                    "rating":0,
                    "nbReviews":0,
                    "publisherName":"DotEmu",
                    "shortDescription":"Let's go back in the 80's with this classic old-school shoot'em up! One of the biggest arcade game will make you travel back in the day. Be ready to have fun with this old-school side-shooter game!",
                    "imageCarousel":"http:\/\/cdn.mobile.nexway.com\/media\/catalog\/product\/s\/c\/screenshot1_5_4.jpg",
                    "icon":"http:\/\/cdn.mobile.nexway.com\/media\/catalog\/product\/2\/0\/2015-02-05_14-37-35.png"
                },
                {
                    "type":"app",
                    "sku":"org.ArmyDelivery",
                    "name":"Army Delivery Files",
                    "priceFormatted":"\u20ac0.91",
                    "price":0.91304631,
                    "rating":0,
                    "nbReviews":0,
                    "publisherName":"Mobile Streams",
                    "shortDescription":"Are you ready for the ultimate gaming experience?\r\nAs soon as you download Army Physics Adventure game you will be amazed how much fun it is. \r\nThis is an amazing forever fun game boosted with secret levels and thrilling packed updates. \r\nCan the world bravest soldier succeed on his mission? This adventure game is all about soldier missions. \r\nLt. Gomez is his name, be ready!",
                    "imageCarousel":"http:\/\/cdn.mobile.nexway.com\/media\/catalog\/product\/b\/a\/banner_14_1_3.png",
                    "icon":"http:\/\/cdn.mobile.nexway.com\/media\/catalog\/product\/i\/c\/icon_27_51.png"
                }
            ]
        }
    ]
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
    "id":"28",
    "name":"Top Jeux action",
    "key":"top-jeux-action",
    "representation":"highlights",
    "options":{
        "quantityLimit":5,
        "showMore":true,
        "showMoreLimit":20
    },
    "products":[
        {
            "type":"app",
            "sku":"com.cravecreative.eastereggjump",
            "name":"Easter Egg Jump",
            "priceFormatted":"\u20ac0.99",
            "price":0.9899635446,
            "rating":0,
            "nbReviews":0,
            "publisherName":"Crave Creative",
            "shortDescription":"Guide the baby chick over the Easter eggs to boost him upward.\r\n",
            "imageCarousel":"http:\/\/cdn.mobile.nexway.com\/media\/catalog\/product\/e\/a\/easter-egg-jump-1024x500.png",
            "icon":"http:\/\/cdn.mobile.nexway.com\/media\/catalog\/product\/e\/a\/easter-egg-jump-icon-512.png"
        },
        {
            "type":"app",
            "sku":"org.jymc.spacegame.FeedTheFishy",
            "name":"Feed The Fishy",
            "priceFormatted":"\u20ac0.91",
            "price":0.91304631,
            "rating":0,
            "nbReviews":0,
            "publisherName":"Mobile Streams",
            "shortDescription":"This a very addictive game, the whole purpose is to help the fishy swim from one point to the other. Energy gets reduced, so you need to eat smaller fishes and other items to boost your energy level.",
            "imageCarousel":"http:\/\/cdn.mobile.nexway.com\/media\/catalog\/product\/t\/i\/title_1_30.png",
            "icon":"http:\/\/cdn.mobile.nexway.com\/media\/catalog\/product\/i\/c\/icon_30_1_12.png"
        },
        {
            "type":"app",
            "sku":"com.jarbull.streetball",
            "name":"Streetball Shootout",
            "priceFormatted":"\u20ac0.91",
            "price":0.91304631,
            "rating":0,
            "nbReviews":0,
            "publisherName":"Spoiled Milk Limited",
            "shortDescription":"Hit the streets instantly and test your basketball skills on the urban courts in STREETBALL SHOOTOUT! Try to score as many shots as you can without missing and try to be the streetball master.",
            "icon":"http:\/\/cdn.mobile.nexway.com\/media\/catalog\/product\/c\/o\/collateral_action_1_productCode_10667_id_15_w_110_h_110_name_wap-110x110_3.jpg"
        },
        {
            "type":"app",
            "sku":"com.dotemu.rtype",
            "name":"R-TYPE",
            "priceFormatted":"\u20ac1.79",
            "price":1.7900319021,
            "rating":0,
            "nbReviews":0,
            "publisherName":"DotEmu",
            "shortDescription":"Let's go back in the 80's with this classic old-school shoot'em up! One of the biggest arcade game will make you travel back in the day. Be ready to have fun with this old-school side-shooter game!",
            "imageCarousel":"http:\/\/cdn.mobile.nexway.com\/media\/catalog\/product\/s\/c\/screenshot1_5_4.jpg",
            "icon":"http:\/\/cdn.mobile.nexway.com\/media\/catalog\/product\/2\/0\/2015-02-05_14-37-35.png"
        },
        {
            "type":"app",
            "sku":"org.ArmyDelivery",
            "name":"Army Delivery Files",
            "priceFormatted":"\u20ac0.91",
            "price":0.91304631,
            "rating":0,
            "nbReviews":0,
            "publisherName":"Mobile Streams",
            "shortDescription":"Are you ready for the ultimate gaming experience?\r\nAs soon as you download Army Physics Adventure game you will be amazed how much fun it is. \r\nThis is an amazing forever fun game boosted with secret levels and thrilling packed updates. \r\nCan the world bravest soldier succeed on his mission? This adventure game is all about soldier missions. \r\nLt. Gomez is his name, be ready!",
            "imageCarousel":"http:\/\/cdn.mobile.nexway.com\/media\/catalog\/product\/b\/a\/banner_14_1_3.png",
            "icon":"http:\/\/cdn.mobile.nexway.com\/media\/catalog\/product\/i\/c\/icon_27_51.png"
        }
    ]
}
```

This endpoint retrieves a specific block and the products associated to it.

### HTTP Request

`GET https://my.appstore.com/api/catalog/featured/block/key/appstore-block/storeId/11/age/0-3`

### Query Parameters

Parameter | Mandatory | Default | Description
--------- | --------- | ------- | -----------
storeId | yes | none | The storeId defines many things, such as the currency, the language, the availability.
key | yes | none | The featured page key.
id  | no | none | The featured block id (this one has priority over `key` parameter if passed).
age | no | all | If you want to filter the output by age range (ex. `0-3`, `3-`)
compatibility | no | all | If you want to filter the output by device screen compatibility. Must be specified as: `4` = 4-inch, `7` = 7-inch, `10` = 10-inch (comma separated).


## Get all products of a given block

> Response example

```json
{
    "products":[
        {
            "type":"app",
            "sku":"com.cravecreative.eastereggjump",
            "name":"Easter Egg Jump",
            "priceFormatted":"\u20ac0.99",
            "price":0.9899635446,
            "rating":0,
            "nbReviews":0,
            "publisherName":"Crave Creative",
            "shortDescription":"Guide the baby chick over the Easter eggs to boost him upward.\r\n",
            "imageCarousel":"http:\/\/cdn.mobile.nexway.com\/media\/catalog\/product\/e\/a\/easter-egg-jump-1024x500.png",
            "icon":"http:\/\/cdn.mobile.nexway.com\/media\/catalog\/product\/e\/a\/easter-egg-jump-icon-512.png"
        },
        {
            "type":"app",
            "sku":"org.jymc.spacegame.FeedTheFishy",
            "name":"Feed The Fishy",
            "priceFormatted":"\u20ac0.91",
            "price":0.91304631,
            "rating":0,
            "nbReviews":0,
            "publisherName":"Mobile Streams",
            "shortDescription":"This a very addictive game, the whole purpose is to help the fishy swim from one point to the other. Energy gets reduced, so you need to eat smaller fishes and other items to boost your energy level.",
            "imageCarousel":"http:\/\/cdn.mobile.nexway.com\/media\/catalog\/product\/t\/i\/title_1_30.png",
            "icon":"http:\/\/cdn.mobile.nexway.com\/media\/catalog\/product\/i\/c\/icon_30_1_12.png"
        }
        ...
    ]
}
```

This endpoint retrieves all the products attached to a block.

### HTTP Request

`GET https://my.appstore.com/api/catalog/featured/products/blockId/28/storeId/11/age/0-3`

### Query Parameters

Parameter | Mandatory | Default | Description
--------- | --------- | ------- | -----------
storeId | yes | none | The storeId defines many things, such as the currency, the language, the availability.
blockId | yes | none | The featured block id.
age | no | all | If you want to filter the output by age range (ex. `0-3`, `3-`)
compatibility | no | all | If you want to filter the output by device screen compatibility. Must be specified as: `4` = 4-inch, `7` = 7-inch, `10` = 10-inch (comma separated).
