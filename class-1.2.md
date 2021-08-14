# Class - 1.2

```json
HEAD catalogo/_doc/1
curl -IHEAD "http://localhost:9200/catalogo/_doc/1"

GET catalogo/_doc/1

PUT catalogo/_doc/50
{
    "nome": "Marcelo Ricardo de Oliveira",
    "interesses": [
        "cinema",
        "música",
        "programação"
    ],
    "cidade": "São Paulo",
    "formação": "Tecnologia da Informação",
    "estado": "SP",
    "país": "Brasil"
}

PUT catalogo/_doc/50
{
    "nome": "Marcelo Ricardo de Oliveira 2",
    "interesses": [
        "cinema",
        "música",
        "programação"
    ],
    "cidade": "São Paulo",
    "formação": "Tecnologia da Informação",
    "estado": "SP",
    "país": "Brasil"
}

POST catalogo/_update/50
{
  "doc": {
    "nome": "Marcelo Ricardo de Oliveira 3"
  }
}

```
