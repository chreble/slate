
# Featured

## Get a specific Page

> Response example

```json
{
    "name": "Darty for you",
    "key": "darty-for-you",
    "options": {
        "pageTitle": ""
    },
    "blocks": [{
        "id": "66",
        "name": "Top Sellers",
        "representation": "list",
        "products": [{
            "type": "app",
            "sku": "air.com.generation5.petitours1",
            "name": "Little Bear",
            "priceFormatted": "23,61 krN",
            "price": 23.6118805,
            "rating": 0,
            "nbReviews": 0,
            "publisherName": "Génération 5",
            "description": "An app developped by experts and endorsed by parents and teachers!\r\nLet your child experience a fun adventure with this early learning touch screen application for toddlers.\r\nAlong with Little Bear, who will accompany the child throughout the games, your baby will experiment with gestures, coordination and sound recognition.\r\nThe games help to develop use of the senses (sight, touch, hearing).\r\nIn a comforting countryside environment, in these four games your baby will:\r\n- discover which animal is hiding behind the screen.\r\n- go hunting for butterflies.\r\n- collect mushrooms and pick flowers.\r\n- recognize objects by the sounds they produce.\r\nAll activities are progressive and difficulty is tailored to each age group.",
            "imageCarousel": "https://kurio.appstore.dev/media/catalog/product/i/m/img_0060.png",
            "icon": "https://kurio.appstore.dev/media/catalog/product/1/1/114.png"
        }, {
            "type": "app",
            "sku": "com.bulkypix.asterix",
            "name": "Asterix Megaslap",
            "priceFormatted": "15,71 krN",
            "price": 15.7149305,
            "rating": 0,
            "nbReviews": 0,
            "publisherName": "Bulkypix",
            "description": "It’s 50 BC and the whole of Gaul is occupied by the Romans… The whole of it? Not quite! That’s because there is a village inhabited by indomitable Gauls that still continues to and always will resist the invader.\r\n\r\nMEGAPUNCH\r\nDrink your magic potion, fire up Asterix’s fist and send your Roman flying as far away as you can.\r\nTHEY’RE CRAZY THESE ROMANS\r\nUnlock more than 20 objects (helmet, cloak, helium, etc.) and characters (Obelix, Dogmatix and other legionaries) which will help send your Roman further and further away.\r\n\r\nTHE WORLD OF ASTERIX\r\nTravel through the most symbolic countries from the adventures of Asterix, from the Gaul village to Egypt via the Compendium Roman camp, Lutetia and, of course, Rome…and not forgetting the pirates, by Jove!\r\n\r\nSIMPLE AND FUN\r\nAsterix Megapunch is intended for Gauls of all ages. Fire up Asterix’s fist by twirling your finger before aiming it at your Roman to send him flying straightaway.\r\n\r\nCOLLECT THE ASTERIX CHARACTERS\r\nCollect the 30 Asterix character cards by picking them up during the levels or swapping them with your friends. Caesar will be happy to tell you their story.\r\n\r\nCHALLENGE YOUR FRIENDS\r\n- Take on your friends. Their records are depicted as Romans inflated with helium that you will encounter on your journey.\r\n",
            "imageCarousel": "https://kurio.appstore.dev/media/catalog/product/f/e/feature_anglais.jpg",
            "icon": "https://kurio.appstore.dev/media/catalog/product/i/c/ico_114x114.png"
        }]
    }, {
        "id": "67",
        "name": "newest",
        "representation": "list",
        "products": [{
            "type": "app",
            "sku": "com.magmamobile.game.RFR",
            "name": "Retro Future Racing",
            "priceFormatted": "free",
            "price": 0,
            "rating": 4,
            "nbReviews": 1,
            "publisherName": "Magma Mobile",
            "description": "A Racing sensation.\r\nBuckle up! You are in for quite a fabulous ride with Retro Future Racing. In this free 3D racing game, you will have the opportunity to drive amazing oldies cars in the most amazing futuristic parallel environment. Will you be able to reach maximum speed on each track?\r\nThis free car racing game includes a gorgeous selection of cars that you can upgrade with great boosts and custom options. The more you play, the more skills you will acquire and the more coins you will collect to make your ride the most beautiful and efficient of them all.\r\nThe game is packed with a wide variety of tracks that will challenge your driving skills. As the game progresses, you will have to be faster and faster and qualify to get a chance to compete against five others cars for the the #1 spot.\r\nThe game physics and dynamics offer an unbelievable sensation of speed. The music and sound effects included also play a big role in giving you a full car race experience. Packed with hours of fun, it will demand amazing skills to complete all the achievements included in the game.\r\nThe game is tablet ready",
            "icon": "https://kurio.appstore.dev/media/catalog/product/a/p/app_icon.png"
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
key | yes | none | The featured page key.
age | no | all | If you want to filter the output by age range (ex. `0-3`, `3-`)
compatibility | no | all | If you want to filter the output by device screen compatibility. Must be specified as: `4` = 4-inch, `7` = 7-inch, `10` = 10-inch (comma separated).

## Get a specific Block

> Response example

```json
{
    "id": "1",
    "name": "Category games",
    "key": "category-games",
    "representation": "list",
    "products": [{
        "type": "app",
        "sku": "sk.inlogic.mania7x7",
        "name": "7x7 Mania!",
        "priceFormatted": "6,99 krN",
        "price": 6.99038014,
        "rating": 0,
        "nbReviews": 0,
        "publisherName": "Inlogic Software",
        "description": "Confectionery experiment gone wrong and jelly cubes are invading your kitchen! It's time to get rid of them. Move them around the table, connect them to form lines of the same color and make them disappear before they crowd the whole table. You can help yourself with features like undo and Move Anywhere. And, of course, there is an indicator of upcoming colors at your disposal. Do you have enough wit and concentration to make it to the higher level?\r\n",
        "imageCarousel": "https://kurio.appstore.dev/media/catalog/product/7/x/7x7mania_preview_1024x500_1.png",
        "icon": "https://kurio.appstore.dev/media/catalog/product/7/x/7x7mania_icon_512x512_1.png"
    }, {
        "type": "app",
        "sku": "com.marbotic.ipad.dixdoigts",
        "name": "10 fingers +",
        "priceFormatted": "15,71 krN",
        "price": 15.7149305,
        "rating": 0,
        "nbReviews": 0,
        "publisherName": "Marbotic",
        "description": "★ Editor's Choice Award 2014 for Excellence in Design - Children's Technology Review\r\n★ 5 stars by theiphonemom : « I thought that by using multitouch, kids could really get a hands-on experience that would help them learn more efficiently. »\r\n★ 4,5/5 stars by BestAppsForKids : « Multitouch feature leads to unique way to help kids build their basic counting and addition skills. »\r\n★ Theimum gave it 4 stars : « This is a very useful digital tool that would complement any learning program involving concrete manipulatives. »\r\n\r\n-----------\r\n\r\nLearn how to count on your fingers by using Multitouch!\r\n\r\n10 fingers offers children an intuitive game so they can become familiar with numbers and numerals. Children can also begin having fun with addition.\r\n\r\nThis innovative app uses the multi-touch feature on the iPad screen. When the child puts 3 fingers onto the screen, the digit \"3\" displays, and the word \"three\" is pronounced.\r\n\r\nThis app is designed for children from 3 to 6 years old. Younger children may enjoy 10 fingers once they start counting \"1, 2, 3\".\r\n\r\nYour child can learn counting in 11 languages : English, French, German, Spanish, Italian...\r\n\r\n\"Free\" mode lets children explore at their own pace: What if I put all my fingers on the screen? What about two fingers from each hand?\r\n\"Challenge\" mode asks the child question, which must be answered by placing the right number of fingers onto the screen.\r\n\r\nThe app is inspired by Montessori pedagogy by promoting the acquisition of abstract concepts using concrete manipulation. A wooden number toy that interacts with the iPad can be used to play with the app and stimulate the child’s senses even further!\r\n\r\n10 fingers trains children in:\r\n-The concept of numbers and quantity\r\n-Visual and auditory recognition of numbers\r\n-The concept of addition\r\n-Motor skills\r\n\r\nThis app has no advertising or in-app purchases. Useful information can be found in a Parents’ Corner.\r\n\r\n10 Fingers is the first product from Marbotic, a publisher that designs and creates innovative educational solutions blending sensory material and digital interfaces.",
        "imageCarousel": "https://kurio.appstore.dev/media/catalog/product/b/a/banner_12_13.png",
        "icon": "https://kurio.appstore.dev/media/catalog/product/i/c/icon_20_11.png"
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
key | yes | none | The featured page key.
age | no | all | If you want to filter the output by age range (ex. `0-3`, `3-`)
compatibility | no | all | If you want to filter the output by device screen compatibility. Must be specified as: `4` = 4-inch, `7` = 7-inch, `10` = 10-inch (comma separated).
