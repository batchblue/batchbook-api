Data Reference
==============

Person XML
------

``` xml
<person>
  <id type="integer">32</id>
  <about>All around cool guy.</about>
  <prefix>Mr.</prefix>
  <first-name>Eric</first-name>
  <middle-name>M</middle-name>
  <last-name>Krause</last-name>
  <emails type="array">
    ...
  </emails>
  <phones type="array">
    ...
  </phones>
  <websites type="array">
    ...
  </websites>
  <addresses type="array">
    ...
  </addresses>
  <tags type="array">
    ...
  </tags>
  <comments type="array">
    ...
  </comments>
  <company-affiliations type="array">
    <company-affiliation>
      <id type="integer">3</id>
      <company-id type="integer">33</company-id>
      <current type="boolean">true</current>
      <job-title>Director of Engineering</job-title>
    </company-affiliation>
  </company-affiliations>
  <cf-records type="array"/>
</person>
```

Person json
-----------
```json
{"person":
  {"id":32,
  "about":"All around cool guy.",
  "prefix":"Mr.",
  "first_name":"Eric",
  "middle_name":"M",
  "last_name":"Krause",
  "emails":[
      ...
    ],
  "phones":[
      ...
    ],
  "websites":[
      ...
    ],
  "addresses":[
      ...
    ],
  "tags":[
      ...
    ],
  "comments":[
      ...
    ],
  "company_affiliations":[
    {"id":3,
    "company_id":33,
    "current":true,
    "job_title":"Director of Engineering"
    }],
  "cf_records":[
    ...
  ]
}
```

Company XML
-----------
``` xml

<company>
  <id type="integer">33</id>
  <about nil="true">A great company to work for.</about>
  <name>Batchbook</name>
  <emails type="array">
    ...
  </emails>
  <phones type="array">
    ...
  </phones>
  <websites type="array">
    ...
  </websites>
  <addresses type="array">
    ...
  </addresses>
  <tags type="array">
    ...
  </tags>
  <comments type="array">
    ...
  </comments>
  <cf-records type="array">
    ...
  </cf-records>
</company>

```

Company JSON
-----------
``` json
{
  "company":
  {
    "id":33,
    "about":"A great company to work for",
    "name":"Batchbook",
    "emails":[
      ...
    ],
    "phones":[
      ...
    ],
    "websites":[
      ...
    ],
    "addresses":[
      ...
    ],
    "tags":[
      ...
    ],
    "comments":[
      ...
    ],
    "cf_records":[
      ...
    ]
  }
}

```

Email XML
---------
``` xml
<email>
  <id type="integer">25</id>
  <address>bar@example.com</address>
  <label>work</label>
</email>
```

Email JSON
---------
``` json
{
  "id":25,
  "address":"bar@example.com",
  "label":"work"
}
```

Website XML
---------
``` xml
<website>
  <id type="integer">62</id>
  <address>http://batchblue.com</address>
  <label>work</label>
</website>
```

Website JSON
---------
``` json
{
  "id":62,
  "address":"http://batchblue.com",
  "label":"work"
}
```

Address XML
---------
``` xml
<address>
  <id type="integer">113</id>
  <address-1>171 Chestnut st</address-1>
  <address-2>2L</address-2>
  <city>Providence</city>
  <state>RI</state>
  <postal-code>02903</postal-code>
  <country>United States</country>
  <label>work</label>
</address>
```

Address JSON
---------
``` json
{
  "id":113,
  "address_1":"171 Chestnut St",
  "address_2":"2L",
  "city":"Providence",
  "state":"RI",
  "postal_code":"02903",
  "country":"United States",
  "label":"work"
}
```

Phone XML
---------
``` xml
<phone>
  <id type="integer">69</id>
  <number>1 401 867 5309</number>
  <label>cell</label>
</phone>
```

Phone JSON
---------
``` json
{
  "id":69,
  "number":"1 401 867 5309",
  "label":"cell"
}
```

Custom Field Set XML
---------
``` xml
<custom-field-set>
  <id type="integer">46</id>
  <name>everything</name>
  <description>my test to convert all supertags to custom fields</description>
  <custom-field-definitions-attributes type="array">
    ...
  </custom-field-definitions-attributes>
</custom-field-set>

```

Custom Field Set JSON
---------
``` json
{
  "custom_field_set":
  {
    "id":46,
    "name":"everything",
    "description":"my test to convert all supertags to custom fields",
    "custom_field_definitions_attributes":[
      ...
    ]
  }
}

```

Custom Field Definition Attribute
-----
``` xml
<custom-field-definitions-attribute>
  <id type="integer">198</id>
  <name>Text Short Field</name>
  <type>Text</type>
  <options>
    <subfields type="array"/>
    <primary type="integer">1</primary>
  </options>
  <position type="integer">3</position>
</custom-field-definitions-attribute>

OR

<custom-field-definitions-attribute>
  <id type="integer">217</id>
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
```

Custom Field Definition Attribute
-----
``` json
{
  "id":198,
  "name":"Text Short Field",
  "type":"Text",
  "options":
  {
    "subfields":[],
    "primary":1
  },
  "position":3
}

OR

{
  "id":217,
  "name":"Checkboxes Multiple Choices",
  "type":"MultipleChoice",
  "options":
  {
    "subfields":["option 1","option 2","option 3"],
    "primary":"3"
  },
  "position":22
}
```



Custom Field Record XML
----

``` xml
<cf-record>
  <id type="integer">81</id>
  <custom-field-set-id type="integer">46</custom-field-set-id>
  <custom-field-values type="array">
    <custom-field-value>
      <id type="integer">51</id>
      <custom-field-definition-id type="integer">198</custom-field-definition-id>
      <text-value>short</text-value>
    </custom-field-value>
    <custom-field-value>
      <id type="integer">33</id>
      <custom-field-definition-id type="integer">199</custom-field-definition-id>
      <text-value>long</text-value>
    </custom-field-value>
    <custom-field-value>
      <id type="integer">32</id>
      <custom-field-definition-id type="integer">200</custom-field-definition-id>
      <decimal-value type="decimal">1234.0</decimal-value>
    </custom-field-value>
    <custom-field-value>
      <id type="integer">48</id>
      <custom-field-definition-id type="integer">201</custom-field-definition-id>
      <boolean-value type="boolean">false</boolean-value>
    </custom-field-value>
    <custom-field-value>
      <id type="integer">38</id>
      <custom-field-definition-id type="integer">202</custom-field-definition-id>
      <text-value>867-5309</text-value>
    </custom-field-value>
    <custom-field-value>
      <id type="integer">39</id>
      <custom-field-definition-id type="integer">203</custom-field-definition-id>
      <text-value>foo@bar.com</text-value>
    </custom-field-value>
    <custom-field-value>
      <id type="integer">35</id>
      <custom-field-definition-id type="integer">204</custom-field-definition-id>
      <text-value>http://foo.com</text-value>
    </custom-field-value>
    <custom-field-value>
      <id type="integer">31</id>
      <custom-field-definition-id type="integer">205</custom-field-definition-id>
      <datetime-value type="datetime">2012-01-18T13:18:00-11:00</datetime-value>
    </custom-field-value>
    <custom-field-value>
      <id type="integer">52</id>
      <custom-field-definition-id type="integer">206</custom-field-definition-id>
      <datetime-value type="datetime">2012-01-25T18:00:00-11:00</datetime-value>
    </custom-field-value>
    <custom-field-value>
      <id type="integer">34</id>
      <custom-field-definition-id type="integer">207</custom-field-definition-id>
      <datetime-value type="datetime">2012-04-15T17:00:00-11:00</datetime-value>
    </custom-field-value>
    <custom-field-value>
      <id type="integer">50</id>
      <custom-field-definition-id type="integer">208</custom-field-definition-id>
      <datetime-value type="datetime">2013-01-24T18:00:00-11:00</datetime-value>
    </custom-field-value>
    <custom-field-value>
      <id type="integer">37</id>
      <custom-field-definition-id type="integer">209</custom-field-definition-id>
      <text-value>http://foo.com/foo.rss</text-value>
    </custom-field-value>
    <custom-field-value>
      <id type="integer">47</id>
      <custom-field-definition-id type="integer">210</custom-field-definition-id>
      <text-value>eric.krause</text-value>
    </custom-field-value>
    <custom-field-value>
      <id type="integer">44</id>
      <custom-field-definition-id type="integer">211</custom-field-definition-id>
      <text-value>http://flicker_something</text-value>
    </custom-field-value>
    <custom-field-value>
      <id type="integer">49</id>
      <custom-field-definition-id type="integer">212</custom-field-definition-id>
      <text-value>http://www.linkedin.com/profile</text-value>
    </custom-field-value>
    <custom-field-value>
      <id type="integer">43</id>
      <custom-field-definition-id type="integer">213</custom-field-definition-id>
      <text-value>erickrause</text-value>
    </custom-field-value>
    <custom-field-value>
      <id type="integer">46</id>
      <custom-field-definition-id type="integer">214</custom-field-definition-id>
      <text-value>http://erickrause</text-value>
    </custom-field-value>
    <custom-field-value>
      <id type="integer">36</id>
      <custom-field-definition-id type="integer">215</custom-field-definition-id>
      <serialized-value>option 1</serialized-value>
    </custom-field-value>
    <custom-field-value>
      <id type="integer">42</id>
      <custom-field-definition-id type="integer">216</custom-field-definition-id>
      <serialized-value>option 2</serialized-value>
    </custom-field-value>
    <custom-field-value>
      <id type="integer">30</id>
      <custom-field-definition-id type="integer">217</custom-field-definition-id>
      <serialized-value type="array">
        <serialized-value>option 1</serialized-value>
        <serialized-value>option 2</serialized-value>
        <serialized-value>option 3</serialized-value>
      </serialized-value>
    </custom-field-value>
    <custom-field-value>
      <id type="integer">45</id>
      <custom-field-definition-id type="integer">218</custom-field-definition-id>
      <decimal-value type="decimal">1234.0</decimal-value>
    </custom-field-value>
    <custom-field-value>
      <id type="integer">41</id>
      <custom-field-definition-id type="integer">219</custom-field-definition-id>
      <integer-value type="integer">11</integer-value>
    </custom-field-value>
    <custom-field-value>
      <id type="integer">40</id>
      <custom-field-definition-id type="integer">220</custom-field-definition-id>
      <decimal-value type="decimal">1.23</decimal-value>
    </custom-field-value>
  </custom-field-values>
</cf-record>
```

Custom Field Record JSON
-------

``` json
{
  "id":81,
  "custom_field_set_id":46,
  "custom_field_values":[
  {
    "id":51,
    "custom_field_definition_id":198,
    "text_value":"short"
  },
  {
    "id":33,
    "custom_field_definition_id":199,
    "text_value":"long"
  },
  {
    "id":32,
    "custom_field_definition_id":200,
    "decimal_value":"1234.0"
  },
  {
    "id":48,
    "custom_field_definition_id":201,
    "boolean_value":false
  },
  {
    "id":38,
    "custom_field_definition_id":202,
    "text_value":"867-5309"
  },
  {
    "id":39,
    "custom_field_definition_id":203,
    "text_value":"foo@bar.com"
  },
  {
    "id":35,
    "custom_field_definition_id":204,
    "text_value":"http://foo.com"
  },
  {
    "id":31,
    "custom_field_definition_id":205,
    "datetime_value":"2012-01-18T13:18:00-11:00"
  },
  {
    "id":52,
    "custom_field_definition_id":206,
    "datetime_value":"2012-01-25T18:00:00-11:00"
  },
  {
    "id":34,
    "custom_field_definition_id":207,
    "datetime_value":"2012-04-15T17:00:00-11:00"
  },
  {
    "id":50,
    "custom_field_definition_id":208,
    "datetime_value":"2013-01-24T18:00:00-11:00"
  },
  {
    "id":37,
    "custom_field_definition_id":209,
    "text_value":"http://foo.com/foo.rss"
  },
  {
    "id":47,
    "custom_field_definition_id":210,
    "text_value":"eric.krause"
  },
  {
    "id":44,
    "custom_field_definition_id":211,
    "text_value":"http://flicker_something"
  },
  {
    "id":49,
    "custom_field_definition_id":212,
    "text_value":"http://www.linkedin.com/profile"
  },
  {
    "id":43,
    "custom_field_definition_id":213,
    "text_value":"erickrause"
  },
  {
    "id":46,
    "custom_field_definition_id":214,
    "text_value":"http://erickrause"
  },
  {
    "id":36,
    "custom_field_definition_id":215,
    "serialized_value":"option 1"
  },
  {
    "id":42,
    "custom_field_definition_id":216,
    "serialized_value":"option 2"
  },
  {
    "id":30,
    "custom_field_definition_id":217,
    "serialized_value":["option 1","option 2","option 3"]
  },
  {
    "id":45,
    "custom_field_definition_id":218,
    "decimal_value":"1234.0"
  },
  {
    "id":41,
    "custom_field_definition_id":219,
    "integer_value":11
  },
  {
    "id":40,
    "custom_field_definition_id":220,
    "decimal_value":"1.23"
  }]
}
```

Tag XML
---------
``` xml
<tag>
  <id type="integer">6</id>
  <name>awesome</name>
</tag>

```

Tag JSON
---------
``` json
{
    "tag":
  {
    "id":6,
    "name":"awesome"
  }
}

```

Comment XML
-----
``` xml
<comment>
  <id type="integer">30</id>
  <comment>A Simple Comment</comment>
  <user-id type="integer">8</user-id>
</comment>
```

Comment JSON
-----
``` json
{
  "id":30,
  "comment":"A Simple Comment",
  "user_id":8
}
```

Roles XML
----
``` xml
<role>
  <id type="integer">1</id>
  <name>Owner</name>
</role>
```

Roles JSON
----
``` json
{
  "id":1,
  "name":"Owner"
}
```

