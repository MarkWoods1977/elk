# es

## search

* Kibana -> dev tools 

### Show all indexes

`GET _search
{
  "size": 0,
  "aggs": {
    "byindex": {
      "terms": {
        "field": "_index"
      }
    }
  }
}`
