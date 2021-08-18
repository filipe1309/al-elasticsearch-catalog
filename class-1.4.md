# Class - 1.4

```json
GET catalogo/_mapping

PUT /catalogo/_doc/1
{
  "nome": "Patrick von Steppat",
  "interesses": [
    "computação",
    "culinária",
    "cinema"
  ],
  "cidade": "Rio de Janeiro",
  "formação": "Gastronomia",
  "estado": "RJ",
  "país": "Brasil"
}

PUT /catalogo/_doc/1
{
  "nome": "Patrick von Steppat 2",
  "interesses": [
    "computação",
    "culinária",
    "cinema"
  ],
  "cidade": "Rio de Janeiro",
  "formação": "Gastronomia",
  "estado": "RJ",
  "país": "Brasil",
  "nascimento": "1984-10-03T12:00:00Z"
}

GET catalogo/_doc/1

GET catalogo/_mapping


POST /catalogo/_doc
{
  "nome": "Super Mario",
  "interesses": [
    "computação",
    "games",
    "carros"
  ],
  "força": 3,
  "velocidade": 55.3,
  "cidade": "Kyoto",
  "formação": "Encanador",
  "estado": "Honshu",
  "país": "Japão",
  "nascimento": "1982-01-21"
}

PUT catalogo/_mapping
{
    "properties": {
        "pulo": {
            "type": "integer"
        }
    }
}
```

https://caelum-online-public.s3.amazonaws.com/1495-elasticsearch1/04/Alura+Elasticsearch+Aula+04_+Mapeamento+de+tipos.pdf
