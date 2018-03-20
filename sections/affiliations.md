Affiliations
=============

### Methods

* [Show](https://github.com/batchblue/batchbook-api/blob/master/sections/affiliations.md#show)
* [Create](https://github.com/batchblue/batchbook-api/blob/master/sections/affiliations.md#create)

[XML Data Reference](https://github.com/batchblue/batchbook-api/blob/master/sections/data_reference.md#affiliation-xml)

[JSON Data Reference](https://github.com/batchblue/batchbook-api/blob/master/sections/data_reference.md#affiliation-json)

Show
---
* `GET /api/v1/affiliations/#{id}.xml or .json` returns a single affiliation.

**Response:**

[XML Data Reference](https://github.com/batchblue/batchbook-api/blob/master/sections/data_reference.md#affiliation-xml)

[JSON Data Reference](https://github.com/batchblue/batchbook-api/blob/master/sections/data_reference.md#affiliation-json)


Create
---

* `POST api/v1/affiliations.xml or .json` creates a new affiliation

**Request:**

```xml
<affiliation>
  <affiliate-id type="integer">1035</affiliate-id>
  <affiliate-type>Contact</affiliate-type>
  <affiliator-id type="integer">1044</affiliator-id>
  <affiliator-type>Contact</affiliator-type>
  <affiliation-type-id type="integer">7</affiliation-type-id>
</affiliation>
```

```json
{
  "affiliation": {
    "affiliate_id":1035,
    "affiliate_type":"Contact",
    "affiliator_id":1044,
    "affiliator_type":"Contact",
    "affiliation_type_id":7
  }
}
```

**Response:**

    Status: 201 Created
    Location: https://your_account.batchbook.com/api/v1/affiliations/the_new_id.{json or xml}

```xml
<affiliation>
  ...
</affiliation>
```

```json
{
  "affiliation":
  {
    "id":the_new_id
    ...
  }
}
```
