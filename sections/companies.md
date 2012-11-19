Companies
=============

### Methods

* [Index](https://github.com/batchblue/batchbook-api/blob/master/sections/companies.md#index)
* [Show](https://github.com/batchblue/batchbook-api/blob/master/sections/companies.md#show)
* [Create](https://github.com/batchblue/batchbook-api/blob/master/sections/companies.md#create)
* [Update](https://github.com/batchblue/batchbook-api/blob/master/sections/companies.md#update)
* [Destroy](https://github.com/batchblue/batchbook-api/blob/master/sections/companies.md#destroy-company)


[XML Data Reference](https://github.com/batchblue/batchbook-api/blob/master/sections/data_reference.md#company-xml)

[JSON Data Reference](https://github.com/batchblue/batchbook-api/blob/master/sections/data_reference.md#company-json)

Index
----
* `GET /api/v1/companies.xml or .json` returns a collection of companies.  Limited to 25
* `GET /api/v1/companies.xml?page=2` returns the next collection of companies.  Limited to 25

If there is particular search action that would make things easier, please let us know at help@batchblue.com

If no companies are found an empty `{"companies":[]}` or `<companies type="array"/>` is returned

**Response:**

``` xml
<companies type="array">
  <company>
    ...
  </company>
  <company>
    ...
  </company>
</companies>
```

Please note that the company element is skipped when part of the array.

```json
{
  "companies":[
    {
      "id":1157,
      "about":null,
      ...
    },
    {
      "id":123,
      "about":"Something",
      ...
    }
  ]
}
```

Show
---
* `GET /api/v1/companies/#{id}.xml or .json` returns a single company.

**Response:**

[XML Data Reference](https://github.com/batchblue/batchbook-api/blob/master/sections/data_reference.md#company-xml)

[JSON Data Reference](https://github.com/batchblue/batchbook-api/blob/master/sections/data_reference.md#company-json)


Create
---

* `POST api/v1/companies.xml or .json` creates a new company

**Request:**

```xml
<company>
  <name>Batchbook Software</name>
  <about>Customer Friendly Relationships</about>
  <emails type="array">
    <email>
      <address>bar@example.com</address>
      <label>work</label>
    </email>
  </emails>
  <phones type="array">
    <phone>
      <number>1 401 867 5309</number>
      <label>cell</label>
    </phone>
  </phones>
  <websites type="array">
    <website>
      <address>http://batchblue.com</address>
      <label>work</label>
    </website>
  </websites>
  <addresses type="array">
    <address>
      <address-1>171 Chestnut st</address-1>
      <address-2>2L</address-2>
      <city>Providence</city>
      <state>RI</state>
      <postal-code>02903</postal-code>
      <country>United States</country>
      <label>work</label>
    </address>
  </addresses>
  <tags type="array">
    <tag>
      <name>fun</name>
    </tag>
  </tags>
  <comments type="array">
    <comment>
      <comment>A Simple Comment</comment>
      <user-id type="integer">8</user-id>
    </comment>
  </comments>
  <cf-records type="array">
    <cf-record>
      <custom-field-set-id type="integer">46</custom-field-set-id>
      <custom-field-values type="array">
        <custom-field-value>
          <custom-field-definition-id type="integer">198</custom-field-definition-id>
          <text-value>something important</text-value>
        </custom-field-value>
        <custom-field-value>
          <custom-field-definition-id type="integer">199</custom-field-definition-id>
          <text-value>also important</text-value>
        </custom-field-value>
      </custom-field-values>
    </cf-record>
  </cf-records>
  <created-at type="datetime">2012-06-19T14:32:20-04:00</created-at>
  <updated-at type="datetime">2012-06-21T17:15:36-04:00</updated-at>
</company>
```

```json
{"company":
  {
  "about":"Customer Friendly Relationships",
  "name":"Batchbook Software",
  "emails":[
    {
      "address":"bar@example.com",
      "label":"work"
    }],
  "phones":[
    {
      "number":"1 401 867 5309",
      "label":"cell"
    }],
  "addresses":[
    {
      "address_1":"171 Chestnut St",
      "address_2":"2L",
      "city":"Providence",
      "state":"RI",
      "postal_code":"02903",
      "country":"United States",
      "label":"work"
    }],
  "websites":[
    {
      "address":"http://batchblue.com",
      "label":"work"
    }],
  "tags":[
    {
      "name":"fun"
    }],
  "comments":[
    {
      "comment":"A Simple Comment",
      "user_id":8
    }],
  "cf_records":[
    {
      "custom_field_set_id":46,
      "custom_field_values":[
      {
        "custom_field_definition_id":198,
        "text_value":"short"
      },
      {
        "custom_field_definition_id":199,
        "text_value":"long"
      }]
    }],
  "created_at":"2012-06-19T14:32:20-04:00",
  "updated_at":"2012-06-21T17:15:36-04:00"
  }
}
```

**Response:**

    Status: 201 Created
    Location: https://your_account.batchbook.com/api/v1/companies/the_new_id.{json or xml}

```xml
<company>
  ...
</company>
```

```json
{
  "company":
  {
    "id":the_new_id
    ...
  }
}
```


Update
-----

* `PUT /api/v1/companies/#{id}.xml or json

Works just like create.  For nested objects without an id, it will create the nested email/webite/etc.  If the nested record contains an id, it will update.  To destroy a nested record, pass in a key of "_destroy" with a value of 1, "1", or true along with the id.  To destroy a tag, just pass "_destroy" with the name of the tag.

**Request:**

```xml
<company>
  <id type="integer">123</id>
  <about>Customer Friendly Relationships</about>
  <name>Batchbook Software</name>
  <emails type="array">
    <email>
      <address>create@example.com</address>
      <label>home</label>
    </email>
    <email>
      <id type="integer">1</id>
      <address>update@example.com</address>
      <label>work</label>
    </email>
    <email>
      <id type="integer">2</id>
      <address>delete@example.com</address>
      <label>work</label>
      <_destroy type="string">"1"</_destroy>
    </email>
  </emails>
  <phones type="array"/>
  <websites type="array"/>
  <addresses type="array"/>
  <tags type="array">
    <tag>
      <name>awesome</name>
    </tag>
    <tag>
      <name>not awesome</name>
      <_destroy type="integer">1</_destroy>
    </tag>
  </tags>
  <comments type="array"/>
  <cf-records type="array"/>
</company>
```

```json
{"company":
  {"id":132,
  "about":"Customer Friendly Relationships",
  "name":"Batchbook Software",
  "emails":[
    {
      "address":"create@example.com",
      "label":"work"
    },
    {
      "id":1,
      "address":"update@example.com",
      "label":"home"
    },
    {
      "id":2,
      "_destroy":1,
      "address":"destroy@example.com"
    }],
  "phones":[],
  "addresses":[],
  "websites":[],
  "tags":[],
  "comments":[],
  "cf_records":[]
  }
}
```

**Response:**

    Status: 200 OK

Destroy company
--------------

* `DELETE /api/v1/companies/#{id}.xml` destroys the company at the referenced URL.

**Response:**

    Status: 200 OK
