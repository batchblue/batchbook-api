Batchbook API
=============

**THIS API IS DEPRECATED AND WILL BE RETIRED SOON.  PLEASE CONTACT US FOR MORE DETAILS BEFORE BEGINNING ANY DEVELOPMENT AGAINST IT**

The BB2 API is a RESTful interface for accessing and modifying your account.It supports both XML and JSON and a ruby library will be provided to help build client functionality.

Endpoints
---------
* [People](https://github.com/batchblue/batchbook-api/blob/master/sections/people.md)
* [Companies](https://github.com/batchblue/batchbook-api/blob/master/sections/companies.md)
* [Custom Fields](https://github.com/batchblue/batchbook-api/blob/master/sections/custom_fields.md)
* [Affiliations](https://github.com/batchblue/batchbook-api/blob/master/sections/affiliations.md)
* [Affiliation Types](https://github.com/batchblue/batchbook-api/blob/master/sections/affiliation_types.md)
* [Users](https://github.com/batchblue/batchbook-api/blob/master/sections/users.md)
* [Roles](https://github.com/batchblue/batchbook-api/blob/master/sections/roles.md)
* [Communications](https://github.com/batchblue/batchbook-api/blob/master/sections/communications.md)

Authentication
--------------
Authentication at launch will be using token authentication.  The api_key for the user will be found at https://account_name.batchbook.com/preferences The api_key must be passed as a query parameter with the key "auth_token".  For example. https://apitest.batchbook.com/api/v1/people.json?auth_token=GR5doLv88FrnLyLGIwok

There has been some work done on implementing oauth2 but it isn't complete at launch.  If you feel this would make things easier for your integration please let us know.

Api Test Account
----------------

If you would like to quickly test some code against the api, you can use our open apitest account at apitest.batchbook.com.  If you would like a personal account to test your integration against please write in to help@batchblue.com.  If you'd like to see how the data is rendering in batchbook you can go to https://apitest.batchbook.com/?auth_token=mXZ8syJrMYHzcxf8j83D

The apitest account has 4 users to use for testing.

  basic@batchblue.com, api key is 6B8YOw9x1tnbKZuUeVkc
  advanced@batchblue.com, GR5doLv88FrnLyLGIwok
  admin@batchblue.com,  mXZ8syJrMYHzcxf8j83D
  owner@batchblue.com, DGJFgqRAmxGRVnM9wtYq

