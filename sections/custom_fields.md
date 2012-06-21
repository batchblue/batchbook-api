Custom Fields
=============

Custom Fields are replacing SuperTags that were in Batchbook Classic.  Like SuperTags, they can be applied to every contact and store any data that you require.  Unlike SuperTags, they will no longer be a tag.  This was to facilitate the ability to add more than one instance of a Custom Field to a record.

Custom Field Set
================

An account has many Custom Field Sets.  Custom Field Sets are the definitions for the applied custom fields.  This will be where you create the Custom Field, and create the Custom Field Definitions that will make up the Custom Field.

[XML Data Reference](https://github.com/batchblue/batchbook-api/blob/master/sections/data_reference.md#custom-field-set-xml)

[JSON Data Reference](https://github.com/batchblue/batchbook-api/blob/master/sections/data_reference.md#custom-field-set-json)

Index
----
* `GET /api/v1/custom_field_sets.xml or .json` returns a collection of Custom Field Sets.  Limited to 25
* `GET /api/v1/custom_field_sets.xml?page=2` returns the next collection of Custom Field Sets.  Limited to 25

If no Custom Field Sets are found an empty `{"custom_field_sets":[]}` or `<custom_field_sets type="array"/>` is returned

**Response:**

```xml
<custom-field-sets type="array">
  <custom-field-set>
    <id type="integer">49</id>
    <name>everything example</name>
    <description>An example for every Custom Field Type</description>
    <custom-field-definitions-attributes type="array">
      <custom-field-definitions-attribute>
        <id type="integer">240</id>
        <name>Text Short Field</name>
        <type>Text</type>
        <options>
          <subfields type="array"/>
          <primary type="integer">1</primary>
        </options>
        <position type="integer">3</position>
      </custom-field-definitions-attribute>
      <custom-field-definitions-attribute>
        <id type="integer">241</id>
        <name>Text Long Field</name>
        <type>Text</type>
        <options>
          <subfields type="array"/>
          <primary type="integer">2</primary>
        </options>
        <position type="integer">4</position>
      </custom-field-definitions-attribute>
      <custom-field-definitions-attribute>
        <id type="integer">242</id>
        <name>Number Field</name>
        <type>Number</type>
        <options>
          <subfields type="array"/>
        </options>
        <position type="integer">5</position>
      </custom-field-definitions-attribute>
      <custom-field-definitions-attribute>
        <id type="integer">243</id>
        <name>Yes Or No Field</name>
        <type>Boolean</type>
        <options>
          <subfields type="array"/>
        </options>
        <position type="integer">6</position>
      </custom-field-definitions-attribute>
      <custom-field-definitions-attribute>
        <id type="integer">244</id>
        <name>Phone Field</name>
        <type>Phone</type>
        <options>
          <subfields type="array"/>
        </options>
        <position type="integer">7</position>
      </custom-field-definitions-attribute>
      <custom-field-definitions-attribute>
        <id type="integer">245</id>
        <name>Email Field</name>
        <type>Email</type>
        <options>
          <subfields type="array"/>
        </options>
        <position type="integer">8</position>
      </custom-field-definitions-attribute>
      <custom-field-definitions-attribute>
        <id type="integer">246</id>
        <name>Website Field</name>
        <type>Url</type>
        <options>
          <subfields type="array"/>
        </options>
        <position type="integer">9</position>
      </custom-field-definitions-attribute>
      <custom-field-definitions-attribute>
        <id type="integer">247</id>
        <name>Date Time Field</name>
        <type>Date</type>
        <options>
          <subfields type="array"/>
          <primary type="integer">1</primary>
        </options>
        <position type="integer">10</position>
      </custom-field-definitions-attribute>
      <custom-field-definitions-attribute>
        <id type="integer">248</id>
        <name>Date Field</name>
        <type>Date</type>
        <options>
          <subfields type="array"/>
          <primary type="integer">2</primary>
        </options>
        <position type="integer">11</position>
      </custom-field-definitions-attribute>
      <custom-field-definitions-attribute>
        <id type="integer">249</id>
        <name>Recurring Weekly Date</name>
        <type>RecurringDate</type>
        <options>
          <subfields type="array"/>
          <primary type="integer">1</primary>
        </options>
        <position type="integer">12</position>
      </custom-field-definitions-attribute>
      <custom-field-definitions-attribute>
        <id type="integer">250</id>
        <name>Recurring Yearly Date</name>
        <type>RecurringDate</type>
        <options>
          <subfields type="array"/>
          <primary type="integer">2</primary>
        </options>
        <position type="integer">13</position>
      </custom-field-definitions-attribute>
      <custom-field-definitions-attribute>
        <id type="integer">251</id>
        <name>Dropdown One Choice</name>
        <type>MultipleChoice</type>
        <options>
          <subfields type="array">
            <subfield>option 1</subfield>
            <subfield>option 2</subfield>
          </subfields>
          <primary>1</primary>
        </options>
        <position type="integer">20</position>
      </custom-field-definitions-attribute>
      <custom-field-definitions-attribute>
        <id type="integer">252</id>
        <name>Radio Once Choice</name>
        <type>MultipleChoice</type>
        <options>
          <subfields type="array">
            <subfield>option 1</subfield>
            <subfield>option 2</subfield>
          </subfields>
          <primary>2</primary>
        </options>
        <position type="integer">21</position>
      </custom-field-definitions-attribute>
      <custom-field-definitions-attribute>
        <id type="integer">253</id>
        <name>Checkboxes Multiple Choices</name>
        <type>MultipleChoice</type>
        <options>
          <subfields type="array">
            <subfield>option 1</subfield>
            <subfield>option 2</subfield>
            <subfield>option 3</subfield>
          </subfields>
          <primary>3</primary>
        </options>
        <position type="integer">22</position>
      </custom-field-definitions-attribute>
      <custom-field-definitions-attribute>
        <id type="integer">254</id>
        <name>Currency Field</name>
        <type>Currency</type>
        <options>
          <subfields type="array"/>
          <primary type="integer">1</primary>
        </options>
        <position type="integer">23</position>
      </custom-field-definitions-attribute>
      <custom-field-definitions-attribute>
        <id type="integer">255</id>
        <name>Assigned To Field</name>
        <type>AssignedTo</type>
        <options>
          <subfields type="array"/>
        </options>
        <position type="integer">24</position>
      </custom-field-definitions-attribute>
      <custom-field-definitions-attribute>
        <id type="integer">256</id>
        <name>Decimal</name>
        <type>Number</type>
        <options>
          <subfields type="array"/>
        </options>
        <position type="integer">25</position>
      </custom-field-definitions-attribute>
    </custom-field-definitions-attributes>
  </custom-field-set>
</custom-field-sets>
```

```json
{
  "custom_field_sets":[
    {
      "custom_field_set":
        {
          "id":49,
          "name":"everything test2",
          "description":"An example for every Custom Field Type",
          "custom_field_definitions_attributes":[
            {
              "id":240,
              "name":"Text Short Field",
              "type":"Text",
              "options":
                {
                  "subfields":[],
                  "primary":1
                },
              "position":3
            },
            {
              "id":241,
              "name":"Text Long Field",
              "type":"Text",
              "options":
                {
                  "subfields":[],
                  "primary":2
                },
              "position":4
            },
            {
              "id":242,
              "name":"Number Field",
              "type":"Number",
              "options":
                {
                  "subfields":[]
                },
              "position":5},
            {
              "id":243,
              "name":"Yes Or No Field",
              "type":"Boolean",
              "options":
                {
                  "subfields":[]
                },
              "position":6
            },
            {
              "id":244,
              "name":"Phone Field",
              "type":"Phone",
              "options":
                {
                  "subfields":[]
                },
              "position":7
            },
            {
              "id":245,
              "name":"Email Field",
              "type":"Email",
              "options":
                {
                  "subfields":[]
                },
              "position":8
            },
            {
              "id":246,
              "name":"Website Field",
              "type":"Url",
              "options":
                {
                  "subfields":[]
                },
              "position":9
            },
            {
              "id":247,
              "name":"Date Time Field",
              "type":"Date",
              "options":
                {
                  "subfields":[],
                  "primary":1
                },
              "position":10
            },
            {
              "id":248,
              "name":"Date Field",
              "type":"Date",
              "options":
                {
                  "subfields":[],
                  "primary":2
                },
              "position":11
            },
            {
              "id":249,
              "name":"Recurring Weekly Date",
              "type":"RecurringDate",
              "options":
                {
                  "subfields":[],
                  "primary":1
                },
              "position":12
            },
            {
              "id":250,
              "name":"Recurring Yearly Date",
              "type":"RecurringDate",
              "options":
                {
                  "subfields":[],
                  "primary":2
                },
              "position":13
            },
            {
              "id":251,
              "name":"Dropdown One Choice",
              "type":"MultipleChoice",
              "options":
                {
                  "subfields":["option 1","option 2"],
                  "primary":"1"
                },
              "position":20
            },
            {
              "id":252,
              "name":"Radio Once Choice",
              "type":"MultipleChoice",
              "options":
                {
                  "subfields":["option 1","option 2"],
                  "primary":"2"
                },
              "position":21
            },
            {
              "id":253,
              "name":"Checkboxes Multiple Choices",
              "type":"MultipleChoice",
              "options":
                {
                  "subfields":["option 1","option 2","option 3"],
                  "primary":"3"
                },
              "position":22
            },
            {
              "id":254,
              "name":"Currency Field",
              "type":"Currency",
              "options":
                {
                  "subfields":[],
                  "primary":1
                },
              "position":23},
            {
              "id":255,
              "name":"Assigned To Field",
              "type":"AssignedTo",
              "options":
                {
                  "subfields":[]
                },
              "position":24
            },
            {
              "id":256,
              "name":"Decimal",
              "type":"Number",
              "options":
                {
                  "subfields":[]
                },
              "position":25
            }
          ]
        }
      }
    ]
  }
```