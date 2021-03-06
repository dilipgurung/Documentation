# REST API: GET profile subprofiles

Warning: You are viewing the documentation for the old REST API. We recommend 
using [version 2](../restv2/rest-api.md) of the REST API.

Subprofiles are to a collection what regular profiles are to a database.
To request the subprofiles that represent a certain profile in a certain
collections you can send an HTTP GET request to the following URL:

`https://api.copernica.com/v1/profile/$id/subprofiles/$collectionID?access_token=xxxx`

The $id should be replaced with the numerical identifier of the profile 
you're requesting the subprofiles of and $collectionID should be replaced
with the identifier of the collection that contains the subprofile.

## Returned fields

This method returns an array of subprofiles of a profile. These subprofiles are JSON objects with the following properties:

- **id**: unique numerical identifier of the subprofile
- **secret**: secret code associated with the subprofile
- **fields**: fields belonging to the subprofile
- **profile**: ID of the profile the subprofile belongs to
- **collection**: ID of the collection the subprofile belongs to
- **created**: timestamp of when the profile was created in YYYY-MM-DD hh:mm:ss format
- **modified**: timestamp of when the profile was last modified in YYYY-MM-DD hh:mm:ss format

## PHP Example

The following PHP script demonstrates how to use the API method.

```php
// dependencies
require_once('copernica_rest_api.php');
  
// change this into your access token
$api = new CopernicaRestApi("your-access-token");

// do the call, and print result
print_r($api->get("profile/1234/subprofiles/321"));
```

The example above requires the [CopernicaRestApi class](rest-php).

## More information

* [List of all API calls](rest-api)
* [GET profile](rest-get-profile)
