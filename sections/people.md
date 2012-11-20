People
=============

### Methods

* [Index](https://github.com/batchblue/batchbook-api/blob/master/sections/people.md#index)
* [Show](https://github.com/batchblue/batchbook-api/blob/master/sections/people.md#show)
* [Create](https://github.com/batchblue/batchbook-api/blob/master/sections/people.md#create)
* [Update](https://github.com/batchblue/batchbook-api/blob/master/sections/people.md#update)
* [Destroy](https://github.com/batchblue/batchbook-api/blob/master/sections/people.md#destroy-person)

[XML Data Reference](https://github.com/batchblue/batchbook-api/blob/master/sections/data_reference.md#person-xml)

[JSON Data Reference](https://github.com/batchblue/batchbook-api/blob/master/sections/data_reference.md#person-json)

Index
----
Each request is limited to 30 people returned.  To query the next collection, use the page parameter listed below.  Note: You can use multiple parameters in one query.  So email=joe.example.com&tags=awesome would return all people that have both the required email and tag.

* `GET /api/v1/people.xml or .json` returns a collection of people.
* `GET /api/v1/people.xml?page=2` returns the next collection of people.
* `GET /api/v1/people.xml?email=joe.smith@example.com` returns the people who have the email address listed.  (This is an exact search.  So searching for @gmail won't work. If there is a request for this, file an issue please)
* `GET /api/v1/people.xml?tags=awesome` returns the people who have the tag address listed.
* `GET /api/v1/people.xml?name=Joe` returns all people who have "Joe" in their name. [Joe Smith, Joey Bag'ODonuts]   Note: This is effectively a LIKE query.
* `GET /api/v1/people.xml?updated_since=2012-11-20T11:05:15-05:00` returns all people who have been updated since the time passed in.
* `GET /api/v1/people.xml?updated_before=2012-11-20T11:05:15-05:00` returns all people who have been updated before the time passed in.
* `GET /api/v1/people.xml?state=RI` Useful if you want to query all of the people who have an address in a particular state.
* `GET /api/v1/people.xml?champion=true` returns a collection of your champions.  You can pass in 'false' to get a listing of people who are not champions.
* `GET /api/v1/people.xml?company_name=Batchblue` returns a collection of people who are employees of 'Batchblue'
* `GET /api/v1/people.xml?company_id=35` returns a collection of people who are employees of company with the id 35

If there is particular search action that would make things easier, please let us know at help@batchblue.com

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
    },
    {
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
  <champion>true</champion>
  <emails type="array">
    <email>
      <address>bar@example.com</address>
      <label>work</label>
      <primary type="boolean">true</primary>
    </email>
  </emails>
  <phones type="array">
    <phone>
      <number>1 401 867 5309</number>
      <label>cell</label>
      <primary type="boolean">true</primary>
    </phone>
  </phones>
  <websites type="array">
    <website>
      <address>http://batchblue.com</address>
      <label>work</label>
      <primary type="boolean">true</primary>
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
      <primary type="boolean">true</primary>
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
  <created-at type="datetime">2012-06-19T14:32:20-04:00</created-at>
  <updated-at type="datetime">2012-06-21T17:15:36-04:00</updated-at>
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
  "champion":true,
  "emails":[
    {
      "address":"bar@example.com",
      "label":"work",
      "primary": true
    }],
  "phones":[
    {
      "number":"1 401 867 5309",
      "label":"cell",
      "primary": true
    }],
  "addresses":[
    {
      "address_1":"171 Chestnut St",
      "address_2":"2L",
      "city":"Providence",
      "state":"RI",
      "postal_code":"02903",
      "country":"United States",
      "label":"work",
      "primary": true
    }],
  "websites":[
    {
      "address":"http://batchblue.com",
      "label":"work",
      "primary": false
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
    }],
  "created_at":"2012-06-19T14:32:20-04:00",
  "updated_at":"2012-06-21T17:15:36-04:00"
  }
}
```

**Response:**

    Status: 201 Created
    Location: https://your_account.batchbook.com/api/v1/people/the_new_id.{json or xml}

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
  <champion>false</champion>
  <emails type="array">
    <email>
      <address>create@example.com</address>
      <label>home</label>
      <primary type="boolean">true</primary>
    </email>
    <email>
      <id type="integer">1</id>
      <address>update@example.com</address>
      <label>work</label>
      <primary type="boolean">false</primary>
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
      "label":"work",
      "primary":true
    },
    {
      "id":1,
      "address":"update@example.com",
      "label":"home",
      "primary":false
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
