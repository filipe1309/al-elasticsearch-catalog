# Class - 2.4

```json
// All docs v1
GET pessoas/_search
```

```json
// All docs v2
GET pessoas/_search
{
  "query": {
    "match_all": {}
  }
}
```

```json
// Field exists in inverted index
GET pessoas/_search
{
  "query": {
    "exists": {
      "field": "cidade"
    }
  }
}
```

```json
// Exact match (SELECT * FROM _doc WHERE estado = 'BA')
GET pessoas/_search
{
  "query": {
    "term": {
      "estado": "BA"
    }
  }
}

// OR
GET pessoas/_search
{
  "query": {
    "term": {
      "estado": {
        "value": "BA"
      }
    }
  }
}
```

```json
// Select some attributes (SELECT nome, cidade, formacao FROM _doc WHERE estado = 'BA')
GET pessoas/_search
{
  "_source": ["nome", "cidade", "formação"],
  "query": {
    "term": {
      "estado": "BA"
    }
  }
}
```
