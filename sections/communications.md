Communications
=============

* [Index](https://github.com/batchblue/batchbook-api/blob/master/sections/communications.md#index)
* [Show](https://github.com/batchblue/batchbook-api/blob/master/sections/communications.md#show)
* [Create](https://github.com/batchblue/batchbook-api/blob/master/sections/communications.md#create)
* [Update](https://github.com/batchblue/batchbook-api/blob/master/sections/communications.md#update)
* [Destroy](https://github.com/batchblue/batchbook-api/blob/master/sections/communications.md#destroy-company)


[XML Data Reference](https://github.com/batchblue/batchbook-api/blob/master/sections/data_reference.md#communication-xml)

[JSON Data Reference](https://github.com/batchblue/batchbook-api/blob/master/sections/data_reference.md#communication-json)

Index
----

Each request is limited to 30 communications returned.  To query the next collection, use the page parameter listed below.  Note: You can use multiple parameters in one query.  So contact_id=123&updated_since=1775-11-10T11:05:15-05:00 would return all communications that the person or company with the id of 123 and have been updated since Nov 10, 1775.

* `GET /api/v1/communications.xml or .json` returns a collection of communications.
* `GET /api/v1/communications.xml?page=2` returns the next collection of communications.
* `GET /api/v1/communications.xml?contact_id=23` returns all of the communications that the person or company '23' is a part of.
* `GET /api/v1/communications.xml?communication_type=email` returns all of the communications of that particular type.  Each customer starts with [phone, note, email, chat]  If you need a list of all types, create an issue and I'll try to add the logic to return them.
* `GET /api/v1/communications.xml?updated_since=2012-11-20T11:05:15-05:00` returns all communications who have been updated since the time passed in.
* `GET /api/v1/communications.xml?updated_before=2012-11-20T11:05:15-05:00` returns all communications who have been updated before the time passed in.
* `GET /api/v1/communications.xml?created_since=2012-11-20T11:05:15-05:00` returns all communications who have been created since the time passed in.
* `GET /api/v1/communications.xml?created_before=2012-11-20T11:05:15-05:00` returns all communications who have been created before the time passed in.


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

Notes about Communications:

Communication -> date:  #The date the communication was to have happened. So you can log a "chat" that happened last week. It's optional, and will default to the current time if left blank.

Communication -> type: Each account starts with "phone", "email", "chat", "note".  But you can create new types by passing in new strings "Twitter" for example.

Participant Types:  "to", "from", "cc", "bcc"  Note: it's possible to attach a bcc to a communication that is a "chat", but they won't be visible via UI unless you change the type to email.  (I can't think of why anyone would want to do this, but the functionality is there.)

Participant Contact_id:  The person or company id that is the participant.  Required if you want to associate the communication with a contact.  Will be returned as nil if the associated contact was deleted.

Participant Contact_name:  Optional Field.  If this field is not passed in, it will be populated by the contact's display name.  If it is passed in, it will override the name displayed for the participant.  (But not actually update the contact's name).  If the contact_name is set, but the contact_id is nil, it will create the association, but not link to a contact.

Permissions can only be set if the user has the role of advanced, admin or owner.  Basic users are automatically given permissions for any communications that they create.
Permission -> user_id:  This is the only required parameter, This is the basic user's id that should have permissions.
Permission -> created_by:  This is the user id of the person who created the permission.  Will default to the user making the api call.  It can be set to another user's id.  It's not recommended to set it, but it can be done.

**Request:**

```xml
<communication>
    <title>Catching up on old times</title>
    <body>So I saw that you were back in town.  Was wondering if we can get together and grab a beer.</body>
    <date type="datetime">2002-11-20T13:10:00-08:00</date>
    <type>email</type>
    <created-at type="datetime">2012-11-21T07:26:51-08:00</created-at>
    <updated-at type="datetime">2012-11-21T07:33:35-08:00</updated-at>
    <tags type="array">
      <tag>
        <name>fun</name>
      </tag>
    </tags>
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
    <permissions type="array">
        <permission>
            <user-id type="integer">32</user-id>
            <user-name>The Basic User</user-name>
            <created-by type="integer">8</created-by>
            <created-by-name>Eric Krause</created-by-name>
        </permission>
    </permissions>
    <participants type="array">
        <participant>
            <type>from</type>
            <contact-id type="integer">4</contact-id>
            <contact-name>Dr. Drew</contact-name>
        </participant>
        <participant>
            <type>to</type>
            <contact-id type="integer">32</contact-id>
            <contact-name>Eric Krause</contact-name>
        </participant>
    </participants>
</communication>

```

```json
{
  "communication": {
    "title": "Catching up on old times",
    "body": "So I saw that you were back in town.  Was wondering if we can get together and grab a beer.",
    "date": "2002-11-20T13:10:37-08:00",
    "type": "email",
    "created_at": "2012-11-21T07:26:51-08:00",
    "updated_at": "2012-11-21T07:26:51-08:00",
    "tags":[
    {
      "name":"beer"
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
    "permissions": [
      {
        "user_name": "The Basic User",
        "created_by": 8,
        "created_by_name": "Eric Krause"
      }
    ],
    "participants": [
      {
          "type": "from",
          "contact_id": 4,
          "contact_name": "Dr. Drew"
      },
      {
          "type": "to",
          "contact_id": 32,
          "contact_name": "Eric Krause"
      }
    ]
  }
}
```

**Response:**

    Status: 201 Created
    Location: https://your_account.batchbook.com/api/v1/communications/the_new_id.{json or xml}

```xml
<communication>
  <id type="integer">the_new_id</id>
  ...
</communication>
```

```json
{
  "communication":
  {
    "id":the_new_id,
    ...
  }
}
```


Update
-----

* `PUT /api/v1/communications/#{id}.xml or json

Works just like create.  For nested objects without an id, it will create the nested tags/cf_records/participants/permissions.  If the nested record contains an id, it will update.  To destroy a nested record, pass in a key of "_destroy" with a value of 1, "1", or true along with the id.  To destroy a tag, just pass "_destroy" with the name of the tag.

**Request:**

```xml
<communication>
    <title>Catching up on old times</title>
    <body>So I saw that you were back in town.  Was wondering if we can get together and grab a beer.</body>
    <date type="datetime">2002-11-20T13:10:00-08:00</date>
    <type>email</type>
    <created-at type="datetime">2012-11-21T07:26:51-08:00</created-at>
    <updated-at type="datetime">2012-11-21T07:33:35-08:00</updated-at>
    <tags type="array">
      <tag>
        <name>fun</name>
      </tag>
    </tags>
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
    <permissions type="array">
        <permission>
            <id type="integer">4357</id>
            <user-id type="integer">32</user-id>
            <user-name>Michelle Wolverton</user-name>
            <created-by type="integer">8</created-by>
            <created-by-name>Eric Krause</created-by-name>
            <_destroy type="string">"1"</_destroy>
        </permission>
    </permissions>
    <participants type="array">
        <participant>
            <id type="integer">175597</id>
            <type>from</type>
            <contact-id type="integer">4</contact-id>
            <contact-name>Adam Tucker</contact-name>
        </participant>
        <participant>
            <id type="integer">175595</id>
            <type>to</type>
            <contact-id type="integer">32</contact-id>
            <contact-name>Eric Michael Krause</contact-name>
        </participant>
        <participant>
            <type>cc</type>
            <contact-id type="integer">66</contact-id>
        </participant>
    </participants>
</communication>
```

```json
{
  "communication": {
    "id": 29351,
    "title": "Catching up on old times",
    "body": "So I saw that you were back in town.  Was wondering if we can get together and grab a beer.",
    "date": "2002-11-20T13:10:37-08:00",
    "type": "email",
    "created_at": "2012-11-21T07:26:51-08:00",
    "updated_at": "2012-11-21T07:26:51-08:00",
    "tags":[
    {
      "name":"beer"
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
    "permissions": [
      {
        "user_id": 32,
        "user_name": "The Basic User",
        "created_by": 8,
        "created_by_name": "Eric Krause"
      }
    ],
    "participants": [
      {
          "id": 175596,
          "type": "from",
          "contact_id": 4,
          "contact_name": "Dr. Drew"
      },
      {
          "id": 175595,
          "type": "to",
          "contact_id": 32,
          "contact_name": "Eric Krause"
      },
      {
          "type": "cc",
          "contact_id": 66,
      }
    ]
  }
}
```

**Response:**

    Status: 200 OK

Destroy communication
--------------

* `DELETE /api/v1/communications/#{id}.xml` destroys the communication at the referenced URL.

**Response:**

    Status: 200 OK
