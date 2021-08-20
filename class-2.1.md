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



DELETE /indice_com_sinonimo

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
                "esporte,futebol,basquete,society,volei"
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
  "text":"eu gosto de praticar esporte"
}

GET /indice_com_sinonimo/_analyze
{
  "analyzer": "sinonimos",
  "text":"Praticantes de esporte"
}

// Problem...
GET /indice_com_sinonimo/_analyze
{
  "analyzer": "sinonimos",
  "text":"Jogadores de basquete"
}

// Fix with indirections
PUT /indice_com_sinonimo_2
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
    "futebol => futebol,society",
    "society => society,futebol",
    "esporte => esporte,futebol,society,volei,basquete"
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

GET /indice_com_sinonimo_2/_analyze
{
  "analyzer": "sinonimos",
  "text":"volei"
}


GET /indice_com_sinonimo_2/_analyze
{
  "analyzer": "sinonimos",
  "text":"futebol"
}

GET /indice_com_sinonimo_2/_analyze
{
  "analyzer": "sinonimos",
  "text":"esporte"
}

// Problem ...
GET /indice_com_sinonimo_2/_analyze
{
  "analyzer": "sinonimos",
  "text":"esportes"
}

DELETE indice_com_sinonimo_2

PUT /indice_com_sinonimo_2
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
    "futebol => futebol,society",
    "society => society,futebol",
    "esporte => esporte,futebol,society,volei,basquete",
    "esportes => esporte,futebol,society,volei,basquete"
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

```

https://www.elastic.co/guide/en/elasticsearch/reference/current/analysis-synonym-tokenfilter.html

Fuzzy Matching (Você quiz dizer...)

https://www.elastic.co/guide/en/elasticsearch/guide/current/fuzzy-matching.html

https://caelum-online-public.s3.amazonaws.com/1601-elasticsearch2/01/Alura+Elasticsearch+Aula+06_+Analyzers+com+Sin%C3%B4nimos.pdf
