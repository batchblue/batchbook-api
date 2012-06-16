People
=============

[XML Data Reference](https://github.com/batchblue/batchbook-api/blob/master/sections/data_reference.md#person-xml)

[JSON Data Reference](https://github.com/batchblue/batchbook-api/blob/master/sections/data_reference.md#person-json)

Index
----
* `GET /api/v1/people.xml or .json` returns a collection of people.  Limited to 25
* `GET /api/v1/people.xml?page=2` returns the next collection of people.  Limited to 25

If no people are found an empty `{"people":[]}` or `<people type="array"/>` is returned

**Response:**

``` xml
<people type="array">
  <person>
    ...
  </person>
  <person>
    ...
  </person>
</people>
```

Please note that the person element is skipped when part of the array.

```json
{
  "people":[
    {
      "id":1157,
      "about":null,
      ...
    }
  ]
}
```

Show
---
* `GET /api/v1/people/#{id}.xml or .json` returns a single person.

**Response:**

[XML Data Reference](https://github.com/batchblue/batchbook-api/blob/master/sections/data_reference.md#person-xml)

[JSON Data Reference](https://github.com/batchblue/batchbook-api/blob/master/sections/data_reference.md#person-json)


Create
---

* `POST api/v1/people.xml or .json` creates a new person

**Request:**

```xml
<person>
  <about>All around cool guy.</about>
  <prefix>Mr.</prefix>
  <first-name>Eric</first-name>
  <middle-name>M</middle-name>
  <last-name>Krause</last-name>
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
      <name>awesome</name>
    </tag>
  </tags>
  <comments type="array">
    <comment>
      <comment>A Simple Comment</comment>
      <user-id type="integer">8</user-id>
    </comment>
  </comments>
  <company-affiliations type="array">
    <company-affiliation>
      <company-id type="integer">33</company-id>
      <current type="boolean">true</current>
      <job-title>Director of Engineering</job-title>
    </company-affiliation>
  </company-affiliations>
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
</person>
```

```json
{"person":
  {"id":32,
  "about":"All around cool guy.",
  "prefix":"Mr.",
  "first_name":"Eric",
  "middle_name":"M",
  "last_name":"Krause",
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
      "name":"awesome"
    }],
  "comments":[
    {
      "comment":"A Simple Comment",
      "user_id":8
    }],
  "company_affiliations":[
    {
      "company_id":33,
      "current":true,
      "job_title":"Director of Engineering"
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
    }]
  }
}
```

**Response:**

    Status: 201 Created
    Location: https://your_account.batchbook.com/api/v1/people/the_new_id

```xml
<person>
  ...
</person>
```

```json
{
  "person":
  {
    "id":the_new_id
    ...
  }
}
```


Update
-----

* `PUT /api/v1/people/#{id}.xml or json

Works just like create.  For nested objects without an id, it will create the nested email/webite/etc.  If the nested record contains an id, it will update.  To destroy a nested record, pass in a key of "_destroy" with a value of 1, "1", or true along with the id.  To destroy a tag, just pass "_destroy" with the name of the tag. 

**Request:**

```xml
<person>
  <id type="integer">123</id>
  <about>All around cool guy.</about>
  <prefix>Mr.</prefix>
  <first-name>Eric</first-name>
  <middle-name>M</middle-name>
  <last-name>Krause</last-name>
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
  <company-affiliations type="array"/>
  <cf-records type="array"/>
</person>
```

```json
{"person":
  {"id":32,
  "about":"All around cool guy.",
  "prefix":"Mr.",
  "first_name":"Eric",
  "middle_name":"M",
  "last_name":"Krause",
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
  "company_affiliations":[],
  "cf_records":[]
  }
}
```

**Response:**

    Status: 200 OK

Destroy person
--------------

* `DELETE /api/v1/people/#{id}.xml` destroys the person at the referenced URL.

**Response:**

    Status: 200 OK
