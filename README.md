Address Labs API
================

Free and simple API to integrate parsing of unstructured United States addresses into your applications. This is a REST-style API that uses JSON for serialization.


Base URL
--------

All URLs start with

    http://api.addresslabs.com/v1/

In case API has to change in backward-incompatible way, we'll bump the version marker and maintain stable support for the old URLs.


JSON only, no XML
-----------------

We only support JSON for serialization of data. JSON format is without root element and we use `snake_case` to describe attribute keys. This means that you have to send `Content-Type: application/json; charset=utf-8` when POSTing or PUTing data.

You'll receive a `415 Unsupported Media Type` response code if you attempt to use a different value for the Content-Type header.

API
---

* [/parsed-address](https://github.com/addresslabs/api-docs/blob/master/sections/parsed-address.md)


Handling errors
---------------

If Address Labs API is having troubles, you might see a 5xx error. 500 means that the app is entirely down, but you might also see 502 Bad Gateway, 503 Service Unavailable, or 504 Gateway Timeout. It's your responsibility in all of these cases to retry your request later.


Help us help you
----------------

If you have a specific feature request or if you found a bug, please use GitHub issues. If you would like to improve this documentation, please fork these docs and send a pull request with modifications.