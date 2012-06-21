Roles
=====

[XML Data Reference](https://github.com/batchblue/batchbook-api/blob/master/sections/data_reference.md#roles-xml)

[JSON Data Reference](https://github.com/batchblue/batchbook-api/blob/master/sections/data_reference.md#roles-json)

Index
----
* `GET /api/v1/roles.xml or .json` returns a collection of roles.

**Response:**

``` xml
<roles type="array">
  <role>
    <id type="integer">1</id>
    <name>Owner</name>
  </role>
  <role>
    <id type="integer">2</id>
    <name>Admin</name>
  </role>
  <role>
    <id type="integer">3</id>
    <name>Advanced</name>
  </role>
  <role>
    <id type="integer">4</id>
    <name>Basic</name>
  </role>
</roles>
```

Please note that the role element is skipped when part of the array.

```json
{
  "role":[
    {
      "id":1,
      "name":"Owner"
    },
    {
      "id":2,
      "name":"Admin"
    },
    {
      "id":3,
      "name":"Advanced"
    },
    {
      "id":4,
      "name":"Basic"
    }
  ]
}
```

Show
---
* `GET /api/v1/roles/#{id}.xml or .json` returns a single role.

**Response:**

[XML Data Reference](https://github.com/batchblue/batchbook-api/blob/master/sections/data_reference.md#roles-xml)

[JSON Data Reference](https://github.com/batchblue/batchbook-api/blob/master/sections/data_reference.md#roles-json)



