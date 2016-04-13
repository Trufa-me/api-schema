# api-schema
A DSL definition of StepWeb API using JSON Schema.

##Person Example Queries

###Basic Leaf Query
```json
{
  "start": 0,
  "count": 10,
  "query": {
    "entity": "company",
    "criteria": {
      "name": "My Corporation",
      "fromDate": "2014-03-15T16:44:53+01:00",
      "toDate": "2016-04-08T16:44:53+01:00"
    }
  }
}
```

###Basic AND Query
```json
{
  "start": 0,
  "count": 10,
  "query": {
    "AND": [
      {
        "entity": "company",
        "criteria": {
          "name": "My Corporation",
          "fromDate": "2014-03-15T16:44:53+01:00",
          "toDate": "2016-04-08T16:44:53+01:00"
        }
      },
      {
        "entity": "education",
        "criteria": {
          "name": "Oxford University"
        }
      }
   ]
  }
}
```

###Basic OR Query
```json
{
  "start": 0,
  "count": 10,
  "query": {
    "OR": [
      {
        "entity": "company",
        "criteria": {
          "name": "My Corporation"
        }
      },
      {
        "entity": "company",
        "criteria": {
          "name": "ACME"
        }
      }
    ]
  }
}
```

###Nested Query
```json
{
  "start": 0,
  "count": 10,
  "query": {
    "OR": [
      {
        "entity": "company",
        "criteria": {
          "name": "My Corporation",
          "fromDate": "2014-03-15T16:44:53+01:00",
          "toDate": "2016-04-08T16:44:53+01:00"
        }
      },
      {
        "AND": [
          {
            "entity": "company",
            "criteria": {
              "name": "ACME"
            }
          },
          {
            "entity": "education",
            "criteria": {
              "name": "Oxford University"
            }
          }
        ]
      }
    ]
  }
}
```


