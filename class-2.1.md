# Class - 2.1

```json


PUT /indice_com_sinonimo
{
  "settings": {
    "index": {
      "number_of_shards": 3,
      "number_of_replicas": 0
    },
    "analysis": {
      "filter": {
        "filtro_de_sinonimos": {
            "type": "synonym",
            "synonyms": [
                "esporte,futebol,society,futeba,pelada"
            ]
        }
      },
      "analyzer": {
        "sinonimos": {
          "tokenizer":  "standard",
          "filter": [
            "lowercase",
            "filtro_de_sinonimos"
          ]
        }
      }
    }
  }
}

GET /indice_com_sinonimo/_analyze
{
  "analyzer": "sinonimos",
  "text": "eu gosto de jogar society"
}

```
