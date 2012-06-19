WORK IN PROGRESS:
================
  This documentation is under development. Please submit an issue (or contact Batchbook) with specific questions that you do not see addressed here. More docs coming soon!

Batchbook API
=============

The BB2 API is a RESTful interface for accessing and modifying your account.It supports both XML and JSON and a ruby library will be provided to help build client functionality.  The API is currently under construction and the following is only a subset of what will eventually be available.

Endpoints
---------

Authentication
--------------
Authentication at launch will be using token authentication.  The api_key for the user will be found at https://account_name.batchbook.com/preferences The api_key must be passed as a query parameter with the key “auth_token”.  For example. https://apitest.batchbook.com/api/v1/people.json?auth_token=GR5doLv88FrnLyLGIwok

Api Wrappers
------------
* [Ruby wrapper by batchblue](https://github.com/batchblue/batchbook)


Curl Examples
-------------

The following is a walkthrough of contacts and custom fields using the "apitest" account on the server.
The apitest account has 4 users to use for testing.

  basic@batchblue.com, api key is 6B8YOw9x1tnbKZuUeVkc
  advanced@batchblue.com, GR5doLv88FrnLyLGIwok
  admin@batchblue.com,  mXZ8syJrMYHzcxf8j83D
  owner@batchblue.com, DGJFgqRAmxGRVnM9wtYq

