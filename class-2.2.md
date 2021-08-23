# Class - 2.2

```json

GET indice_com_sinonimo_2/_analyze
{
  "analyzer": "portuguese",
  "text": "esporte"
}

PUT /catalogo_v3
{
  "settings": {
    "index": {
      "number_of_shards": 3,
      "number_of_replicas": 0
    },
    "analysis": {
      "filter": {
        "portuguese_stop": {
          "type": "stop",
          "stopwords": "_portuguese_"
        },
        "portuguese_stemmer": {
          "type": "stemmer",
          "language": "light_portuguese"
        },
        "filtro_de_sinonimos": {
          "type": "synonym",
          "synonyms": [
            "futebol => futebol,society",
            "society => society,futebol",
            "volei,voleibol,volleyball",
            "esport => esport,futebol,society,volei,basquet",
            "exat => exat,matematic,fisic,computaca",
            "arte => arte,pintur,teatr,music,cinem"
          ]
        }
      },
      "analyzer": {
        "sinonimos": {
          "tokenizer": "standard",
          "filter": [
            "lowercase",
            "portuguese_stop",
            "portuguese_stemmer",
            "filtro_de_sinonimos"
          ]
        }
      }
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
        "analyzer": "portuguese",
        "search_analyzer": "sinonimos"
      },
      "nome": {
        "type": "text",
        "fields": {
          "original": {
            "type": "keyword",
            "index": true
          }
        },
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

POST /catalogo_v3/_doc/1
{
    "nome": "João Silva",
    "interesses": ["futebol", "música", "literatura"],
    "cidade": "São Paulo",
    "formação": "Letras",
    "estado": "SP",
    "país": "Brasil"
}

POST /catalogo_v3/_doc/2
{
    "nome": "Maria Silva",
    "interesses": ["pintura", "literatura", "teatro"],
    "cidade": "Diamantina",
    "formação": "Artes Plásticas",
    "estado": "MG",
    "país": "Brasil"
}

POST /catalogo_v3/_doc/3
{
    "nome": "Richard Edward",
    "interesses": ["matemática", "física", "música"],
    "cidade": "Boston",
    "formação": "Física",
    "estado": "MA",
    "país": "Estados Unidos"
}

POST /catalogo_v3/_doc/4
{
    "nome": "Patrick von Steppat",
    "interesses": ["computação", "culinária", "cinema"],
    "cidade": "Rio de Janeiro",
    "formação": "Gastronomia",
    "estado": "RJ",
    "país": "Brasil"
}

POST /catalogo_v3/_doc/5
{
  "nome": "Paulo Eduardo de Azevedo Silveira",
  "interesses": ["computação", "literatura"],
  "cidade": "São Paulo",
  "formação": "Computação",
  "estado": "SP",
  "país": "Brasil"
}

POST /catalogo_v3/_doc/6
{
  "nome": "Michael Jordan",
  "interesses": ["basquete"],
  "cidade": "Chicago",
  "formação": "Artes",
  "estado": "IL",
  "país": "Estados Unidos"
}

POST /catalogo_v3/_doc/7
{
  "nome": "Marcelo Negrão",
  "interesses": ["volei"],
  "cidade": "São Paulo",
  "formação": "Adminstração",
  "estado": "SP",
  "país": "Brasil"
}

GET /catalogo_v3/_search?q=interesses:esportes

GET /catalogo_v3/_search?q=interesses:exatas
```

https://caelum-online-public.s3.amazonaws.com/1601-elasticsearch2/02/Alura+Elasticsearch+Aula+07_+Adicionando+sin%C3%B4nimos+ao+nosso+cat%C3%A1logo.pdf
