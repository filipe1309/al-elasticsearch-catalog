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

```json
// Combinining criteria (SELECT nome, cidade, formacao FROM _doc WHERE estado = 'BA' AND formacao = 'fisica')
// Options: must, should, must_not, filter
GET pessoas/_search
{
  "_source": ["nome", "cidade", "formação"],
  "query": {
    "bool": {
      "must": [
        { "term": { "estado": "BA" } }, // Is not analyzed
        { "term": { "formação": "fisic" } } // Is analyzed
      ]
    }
  }
}

GET pessoas/_search
{
  "_source": ["nome", "cidade", "formação"],
  "query": {
    "bool": {
      "must": [
        { "term": { "estado": "BA" } }, // Is not analyzed
        { "term": { "formação.original": "Física" } } // Is analyzed
      ]
    }
  }
}

// "formação": "Física" has a higher score
GET pessoas/_search
{
  "_source": ["nome", "cidade", "formação"],
  "query": {
    "bool": {
      "must": [
        { "term": { "estado": "BA" } } // Is not analyzed
      ],
      "should": [
        { "term": { "formação.original": "Física" } }
      ]
    }
  }
}
```
