Data Reference
==============

Person
------

``` xml
<person>
  <id type="integer">32</id>
  <about>All around cool guy.</about>
  <prefix></prefix>
  <first-name>Eric</first-name>
  <middle-name>M</middle-name>
  <last-name>Krause</last-name>
  <emails type="array">
    <email>
      <id type="integer">49</id>
      <address>ekrause@batchblue.com</address>
      <label>work</label>
    </email>
  </emails>
  <phones type="array">
    <phone>
      <id type="integer">48</id>
      <number>401 867-5309</number>
      <label>work</label>
    </phone>
  </phones>
  <websites type="array">
    <website>
      <id type="integer">27</id>
      <address>http://batchbook.com</address>
      <label>work</label>
    </website>
  </websites>
  <addresses type="array">
    <address>
      <id type="integer">27</id>
      <address-1>171 Chestnut St</address-1>
      <address-2></address-2>
      <city>Providence</city>
      <state>RI</state>
      <postal-code>02903</postal-code>
      <country>United States</country>
      <label>work</label>
    </address>
  </addresses>
  <tags type="array">
    <tag>
      <id type="integer">6</id>
      <name>awesome</name>
    </tag>
    <tag>
      <id type="integer">7</id>
      <name>dev</name>
    </tag>
  </tags>
  <comments type="array"/>
  <company-affiliations type="array">
    <company-affiliation>
      <id type="integer">3</id>
      <company-id type="integer">33</company-id>
      <current type="boolean">true</current>
      <job-title>Director of Engineering</job-title>
    </company-affiliation>
  </company-affiliations>
  <cf-records type="array"/>
  <etag>1e6729bb76c8be91038dc8e13d3bd1e6</etag>
</person>
```

```json
{"person":
  {"id":32,
  "about":"All around cool guy.",
  "prefix":"",
  "first_name":"Eric",
  "middle_name":"M",
  "last_name":"Krause",
  "emails":[
    {"id":49,
    "address":"ekrause@batchblue.com",
    "label":"work"
    }],
  "phones":[
    {"id":48,
    "number":"401 867-5309",
    "label":"work"
    }],
  "websites":[
    {"id":27,
    "address":"http://batchbook.com",
    "label":"work"
    }],
  "addresses":[
    {"id":27,
    "address_1":"171 Chestnut St",
    "address_2":"",
    "city":"Providence",
    "state":"RI",
    "postal_code":"02903",
    "country":"United States",
    "label":"work"
    }],
  "tags":[
    {"id":6,
    "name":"awesome"
    },
    {"id":7,
    "name":"dev"}
    ],
  "comments":[],
  "company_affiliations":[
    {"id":3,
    "company_id":33,
    "current":true,
    "job_title":"Director of Engineering"
    }],
  "cf_records":[],
  "etag":"1e6729bb76c8be91038dc8e13d3bd1e6"}
}
```
