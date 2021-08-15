# Class - 1.3

```json
// Default Search, build a string containing all the words in the document
_all

// Free Search
GET catalogo/_search/?q=futebol

// Specific Search
GET catalogo/_search/?q=estado:SP

// Pagination
GET catalogo/_search/?q=futebol&size=10&from=0
GET catalogo/_search/?q=futebol&size=10&from=10
GET catalogo/_search/?q=futebol&size=10&from=20
GET catalogo/_search/?q=futebol&size=10&from=30

```

https://www.elastic.co/guide/en/elasticsearch/reference/current/search-request-scroll.html

https://caelum-online-public.s3.amazonaws.com/1495-elasticsearch1/03/Alura+Elasticsearch+Aula+03_+Os+campos+e+sua+rela%C3%A7%C3%A3o+com+as+buscas.pdf
