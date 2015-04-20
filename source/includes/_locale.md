# Locale

## Get a list of countries

```shell
curl -X GET "https://my.appstore.com/api/locale/country/list"
```

> The above command returns JSON structured like this:

```json
{
    "countries": [{
        "countryId": "US",
        "name": "États-Unis",
        "iso2Code": "US",
        "iso3Code": "USA",
        "isRegionRequired": true,
        "currency": "USD"
    }, {
        "countryId": "GB",
        "name": "Royaume-Uni",
        "iso2Code": "GB",
        "iso3Code": "GBR",
        "isRegionRequired": false,
        "currency": "EURO"
    }]
}
```

This endpoint retrieves a list of countries.  

### HTTP Request

`GET https://my.appstore.com/api/locale/country/list`

## Get a list of regions

```shell
curl -X GET "https://my.appstore.com/api/locale/region/list/countryId/FR"
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

### Query Parameters

Parameter | Mandatory | Default | Description
--------- | --------- | ------- | -----------
countryId | yes | none | The country formatted in two letters, ex. FR, PL.
