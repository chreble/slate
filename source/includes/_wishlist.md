# Wishlist

## Get the wishlist

> Response example

```json
{
    "apps": [{
        "sku": "com.magmamobile.game.IceCream",
        "name": "Ice Cream",
        "description": "Do you like to indulge? Well we have a treat for you. The most delicious Ice Cream game is now available on your mobile phone. You fingers won’t be able to resist it. 

            As a proud owner of an Ice Cream Stand,
        your job is to prepare the most intricate ice cream cones in a record time.Disappointing customer is no option
        for the future of your business.Take orders and make them happen as fast as possible.The more customers you look after,
        the more intricate the orders will be.

        Your memory skills will be challenged all throughout the game.Also,
        as you progress through this fun game,
        you will unlock new ingredients making levels harder and harder to complete.Do you think you are ready to keep up with such intense pace ?

        With the global leaderboard,
        you will be competing against other players all over the world.Can you make it to the top and be crowned the best Ice Cream Parlor in the world ?

        Ice Cream is a free game
        for adults and children alike

        Features :
        -Over 100 Levels of increasing difficulty - Tons of flavors and toppings to choose from - Over 30 achievements to unlock - Global Leaderboard - The Game is Tablet ready and supports over 15 + Languages

        Don’ t wait
        for summer time,
        change up your mind now with Ice Cream!",
        "price" : 0,
        "currency": "EUR",
        "priceFormatted": "free",
        "rating": 1,
        "publisherName": "Magma Mobile",
        "nbReviews": 1,
        "medias": {
            "image": "https://darty.appstore.dev/media/catalog/product/a/p/app_icon_2.png"
        }
    }]
}
```

This endpoint retrieves the customer's wishlist.  

### HTTP Request

`GET https://my.appstore.com/api/wishlist/index`

### Auth Required

`YES`

## Add a product in the wishlist

> Response example

```json
{
  "success": true
}
```

This endpoint adds a product to the customer's wishlist.

### HTTP Request

`POST https://my.appstore.com/api/wishlist/add`

### Auth Required

`YES`

### JSON Request Parameters

Parameter | Mandatory | Default | Description
--------- | --------- | ------- | -----------
sku | yes | none | The application SKU.

## Delete a product in the wishlist

> Response example

```json
{
  "success": true
}
```

This endpoint deletes a product from the customer's wishlist.

### HTTP Request

`POST https://my.appstore.com/api/wishlist/delete`

### Auth Required

`YES`

### JSON Request Parameters

Parameter | Mandatory | Default | Description
--------- | --------- | ------- | -----------
sku | yes | none | The application SKU.