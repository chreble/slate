# API common error codes

The API has built-in standardized error messages and a specific code is returned when the API encounters any kind of error, could be validation error, data mismatch or unhandled exception.

You'll find in the list below, the error codes common to all API services and specific service error codes will be found in the API documentation. 

Code | Meaning
---------- | -------
0001 | Invalid Action
0002 | Invalid Method `%s` expected `%s`
0003 | Unhandled error `%s`
0004 | Invalid Sub Account
1001 | Required parameter `paymentMethod`
1002 | Parameter `%s` can't be empty
1003 | The parameter `%s` expects the exact value `%s`
1004 | The parameter `%s` expects a specific length `%s`
1005 | The parameter `%s` expects a specific format `%s`
1006 | The parameter `%s` has an invalid value, expected `%s`
1007 | Configuration error: `%s`
1008 | Passwords don't match
1009 | The parameter `%s` expects a valid email address
4002 | CDN Provider error `%s`