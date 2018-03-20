Affiliation Types
=============

### Methods

* [Show](https://github.com/batchblue/batchbook-api/blob/master/sections/affiliation_types.md#show)
* [Create](https://github.com/batchblue/batchbook-api/blob/master/sections/affiliation_types.md#create)

[XML Data Reference](https://github.com/batchblue/batchbook-api/blob/master/sections/data_reference.md#affiliation-type-xml)

[JSON Data Reference](https://github.com/batchblue/batchbook-api/blob/master/sections/data_reference.md#affiliation-type-json)

Show
---
* `GET /api/v1/affiliation_types/#{id}.xml or .json` returns a single affiliation type.

**Response:**

[XML Data Reference](https://github.com/batchblue/batchbook-api/blob/master/sections/data_reference.md#affiliation-xml)

[JSON Data Reference](https://github.com/batchblue/batchbook-api/blob/master/sections/data_reference.md#affiliation-json)


Create
---

* `POST api/v1/affiliation_types.xml or .json` creates a new affiliation type

**Request:**

```xml
<affiliation-type>
  <id type="integer">8</id>
  <name>Parent</name>
  <reciprocal-name>Child</reciprocal-name>
</affiliation>
```

```json
{
  "affiliation_type": {
    "id":8,
    "name":"Parent",
    "reciprocal_name":"Child"
  }
}
```

**Response:**

    Status: 201 Created
    Location: https://your_account.batchbook.com/api/v1/affiliation_types/the_new_id.{json or xml}

```xml
<affiliation-type>
  ...
</affiliation-type>
```

```json
{
  "affiliation_type":
  {
    "id":the_new_id
    ...
  }
}
```
