# Class - 1.5

```json
GET catalogo/_search/?q=musica

GET catalogo/_search/?q=música

// Standard analyzer
GET catalogo/_analyze
{
  "text": "Eu nasci há 10 mil (sim, isso mesmo, 10 mil) anos atrás"
}

// Simple analyzer
GET catalogo/_analyze
{
  "analyzer": "simple",
  "text": "Eu nasci há 10 mil (sim, isso mesmo, 10 mil) anos atrás"
}

// Whitespace analyzer
GET catalogo/_analyze
{
  "analyzer": "whitespace",
  "text": "Eu nasci há 10 mil (sim, isso mesmo, 10 mil) anos atrás"
}

// Portuguese analyzer
GET catalogo/_analyze
{
  "analyzer": "portuguese",
  "text": "Eu nasci há 10 mil (sim, isso mesmo, 10 mil) anos atrás"
}

PUT /catalogo_v2
{
  "settings": {
    "index": {
      "number_of_shards": 3,
      "number_of_replicas": 0
    }
  },
  "mappings": {
    "properties": {
      "cidade": {
        "type": "text",
        "index": true,
        "analyzer": "portuguese"
      },
      "estado": {
        "type": "text"
      },
      "formação": {
        "type": "text",
        "index": true,
        "analyzer": "portuguese"
      },
      "interesses": {
        "type": "text",
        "index": true,
        "analyzer": "portuguese"
      },
      "nome": {
        "type": "text",
        "index": true,
        "analyzer": "portuguese"
      },
      "país": {
        "type": "text",
        "index": true,
        "analyzer": "portuguese"
      }
    }
  }
}

POST /catalogo_v2/_doc/1
{
    "nome": "João Silva",
    "interesses": ["futebol", "música", "literatura"],
    "cidade": "São Paulo",
    "formação": "Letras",
    "estado": "SP",
    "país": "Brasil"
}

GET catalogo/_search?q=musica

GET catalogo_v2/_search?q=MÚSICAS

GET /catalogo_v2/_search?q=musica+AND+brasil
```

https://caelum-online-public.s3.amazonaws.com/1495-elasticsearch1/05/Alura+Elasticsearch+Aula+05_+Quebrando+textos+com+Analyzers.pdf
