Users
=====

[XML Data Reference](https://github.com/batchblue/batchbook-api/blob/master/sections/data_reference.md#users-xml)

[JSON Data Reference](https://github.com/batchblue/batchbook-api/blob/master/sections/data_reference.md#users-json)

Index
----
* `GET /api/v1/users.xml or .json` returns a collection of users.  Limited to 25
* `GET /api/v1/users.xml?page=2` returns the next collection of users.  Limited to 25

If no users are found an empty `{"users":[]}` or `<users type="array"/>` is returned

**Response:**

``` xml
<users type="array">
  <user>
    ...
  </user>
  <user>
    ...
  </user>
</users>
```

Please note that the user element is skipped when part of the array.

```json
{
  "user":[
    {
      "id":1157,
      "first_name":"Bob",
      "email":"bob@example.com",
      ...
    },
    {
      "id":123,
      ...
    }
  ]
}
```

Show
---
* `GET /api/v1/users/#{id}.xml or .json` returns a single user.

**Response:**

[XML Data Reference](https://github.com/batchblue/batchbook-api/blob/master/sections/data_reference.md#users-xml)

[JSON Data Reference](https://github.com/batchblue/batchbook-api/blob/master/sections/data_reference.md#users-json)



