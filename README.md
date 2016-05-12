# api-schema
A DSL definition of StepWeb API using JSON Schema.

##Person Example Queries

###Basic Leaf Query
```json
{
  "start": 0,
  "count": 10,
  "query": {
    "entity": "experience",
    "criteria": {
      "company": "My Corporation",
      "start": {
        "from": "2014-03-15T16:44:53+01:00"
      },
      "end": {
        "to": "2016-04-08T16:44:53+01:00"
      }
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
        "entity": "experience",
        "criteria": {
          "company": "My Corporation",
          "start": {
            "from": "2014-03-15T16:44:53+01:00"
          },
          "end": {
            "to": "2016-04-08T16:44:53+01:00"
          }
        }
      },
      {
        "entity": "education",
        "criteria": {
          "establishment": "Oxford University"
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
        "entity": "experience",
        "criteria": {
          "company": "My Corporation"
        }
      },
      {
        "entity": "experience",
        "criteria": {
          "company": "ACME"
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
        "entity": "experience",
        "criteria": {
          "company": "My Corporation",
          "start": {
            "from": "2014-03-15T16:44:53+01:00"
          },
          "end": {
            "to": "2016-04-08T16:44:53+01:00"
          }
        }
      },
      {
        "AND": [
          {
            "entity": "experience",
            "criteria": {
              "company": "ACME"
            }
          },
          {
            "entity": "education",
            "criteria": {
              "establishment": "Oxford University"
            }
          }
        ]
      }
    ]
  }
}
```

### Date Range Query
```json
{
  "start": 0,
  "count": 10,
  "query": {
    {
      "entity": "experience",
      "criteria": {
        "company": "My Corporation",
        "start": {
          "from": "2014-03-15T16:44:53+01:00",
          "to": "2014-09-15T16:44:53+01:00"
        },
        "end": {
          "from": "2016-01-08T16:44:53+01:00",
          "to": "2016-04-08T16:44:53+01:00"
        }
      }
    }
  }
}
```


