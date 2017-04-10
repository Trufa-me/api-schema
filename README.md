# api-schema
A DSL definition of StepWeb API using JSON Schema.

## Person

### Properties
* __start _(integer)___ - Starting index to offset results from.
* __count _(integer)___ - Maximum number of results to return.
* __expand _(boolean)___ - `false` (default) returns summary profiles, `true` returns complete profiles.
* __query _(object)___ - Definition of the query. See below for examples.

### Query Examples

#### Basic Leaf Query
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

#### Basic 'Has Field' Query
```json
{
  "start": 0,
  "count": 10,
  "query": {
    "entity": "email",
    "criteria": {
      "exists": true
    }
  }
}
```

#### Basic AND Query
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

#### Basic OR Query
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

#### Nested Query
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

#### Date Range Query
```json
{
  "start": 0,
  "count": 10,
  "query": {
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
```


