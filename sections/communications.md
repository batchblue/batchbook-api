Communications
=============

[XML Data Reference](https://github.com/batchblue/batchbook-api/blob/master/sections/data_reference.md#communication-xml)

[JSON Data Reference](https://github.com/batchblue/batchbook-api/blob/master/sections/data_reference.md#communication-json)

Index
----
* `GET /api/v1/communications.xml or .json` returns a collection of communications.  Limited to 25
* `GET /api/v1/communications.xml?page=2` returns the next collection of communications.  Limited to 25

If there is particular search action that would make things easier, please let us know at help@batchblue.com

If no communications are found an empty `{"communications":[]}` or `<communications type="array"/>` is returned

**Response:**

``` xml
<communications type="array">
  <communication>
    ...
  </communication>
  <communication>
    ...
  </communication>
</communications>
```

Please note that the communication element is skipped when part of the array.

```json
{
  "communications":[
    {
      "id":1157,
      "title":null,
      ...
    },
    {
      "id":123,
      "title":"Something",
      ...
    }
  ]
}
```

Show
---
* `GET /api/v1/communications/#{id}.xml or .json` returns a single communication.

**Response:**

[XML Data Reference](https://github.com/batchblue/batchbook-api/blob/master/sections/data_reference.md#communication-xml)

[JSON Data Reference](https://github.com/batchblue/batchbook-api/blob/master/sections/data_reference.md#communication-json)


Create
---

* `POST api/v1/communications.xml or .json` creates a new communication

**Request:**

```xml
<communication>
*TODO*
</communication>
```

```json
{"communication":
TODO
}
```

**Response:**

    Status: 201 Created
    Location: https://your_account.batchbook.com/api/v1/communications/the_new_id.{json or xml}

```xml
<communication>
  ...
</communication>
```

```json
{
  "communication":
  {
TODO
  }
}
```


Update
-----

* `PUT /api/v1/communications/#{id}.xml or json

Works just like create.  For nested objects without an id, it will create the nested email/webite/etc.  If the nested record contains an id, it will update.  To destroy a nested record, pass in a key of "_destroy" with a value of 1, "1", or true along with the id.  To destroy a tag, just pass "_destroy" with the name of the tag.

**Request:**

```xml
<communication>
TODO
</communication>
```

```json
{"communication":
TODO
}
```

**Response:**

    Status: 200 OK

Destroy communication
--------------

* `DELETE /api/v1/communications/#{id}.xml` destroys the communication at the referenced URL.

**Response:**

    Status: 200 OK
