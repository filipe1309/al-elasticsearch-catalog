# Class - 2.4

```json
// All docs v1
// SELECT * from _docs
GET pessoas/_search
```

```json
// All docs v2
// SELECT * from _docs
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
// Exact match
// SELECT * FROM _doc WHERE estado = 'BA'
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
// Select some attributes
// SELECT nome, cidade, formacao FROM _doc WHERE estado = 'BA'
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
// Combinining criteria
// SELECT nome, cidade, formacao FROM _doc WHERE estado = 'BA' AND formacao = 'fisica'
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

// Must
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

// Shuold
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

```json
// Must not
GET pessoas/_search
{
  "_source": ["nome", "cidade", "formação"],
  "query": {
    "bool": {
      "must": [
        { "term": { "estado": "BA" } } // Is not analyzed
      ],
      "must_not": [
        { "term": { "formação.original": "Física" } }
      ]
    }
  }
}
```

```json
// Filter
GET pessoas/_search
{
  "_source": ["nome", "cidade", "formação"],
  "query": {
    "bool": {
      "must": [
        { "term": { "estado": "BA" } } // Is not analyzed
      ],
      "must_not": [
        { "term": { "formação.original": "Física" } }
      ],
      "filter": {
        "range": {
          "nome.original": {
            "gte": "A",
            "lte": "Czzzzzz"
          }
        }
      }
    }
  }
}
```

```json
// Non exact match
// SELECT nome, cidade, formacao FROM _doc WHERE estado = 'BA' AND formacao LIKE '%fisica%'
GET pessoas/_search
{
  "_source": ["nome", "cidade", "formação"],
  "query": {
    "bool": {
      "must": [
        { "term": { "estado": "BA" } }, // Is not analyzed
        { "match": { "formação": "Física" } }
      ]
    }
  }
}
```

```json
// Sort results
// SELECT nome, cidade, formacao FROM _doc WHERE estado = 'BA' AND formacao LIKE '%fisica%' ORDER BY cidade ASC, nome DESC
GET pessoas/_search
{
  "_source": ["nome", "cidade", "formação"],
  "query": {
    "bool": {
      "must": [
        { "term": { "estado": "BA" } }, // Is not analyzed
        { "match": { "formação": "Física" } }
      ]
    }
  },
  "sort": [
    { "cidade.original": { "order": "asc" } },
    { "nome.original": "desc" }
  ]
}
```

```json
// Aggregations (group by, count, sum, avg, min, max)
// SELECT estado, count(*) FROM _doc WHERE formacao LIKE '%fisica%' GROUP BY estado
GET pessoas/_search
{
  "query": {
    "match": { "formação": "Física" }
  },
  "aggs": {
    "pessoas formada em fisica por estado": {
      "terms": {
        "field": "estado"
      }
    }
  }
}
```

https://www.elastic.co/guide/en/kibana/current/settings.html

https://caelum-online-public.s3.amazonaws.com/1601-elasticsearch2/04/Alura+Elasticsearch+Aula+09_+Linguagem+de+Consultas.pdf
