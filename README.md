Like anything else, if you don't use it - you lose it. This is a quick reminder of how to use Elasticsearch's basic APIs.

## Index CRUD
- GET /_cat/indices?v
- PUT /{index}
- GET /{index}
- DELETE /{index}

## Indexing
#### Single
- POST /{index}/{type}
{ "name": "doc 1" }

#### Bulk
- POST /_bulk
{ "index": { "_type": "mytype", "_index": "myindex" } }
{ "name": "doc 2" }
{ "index": { "_type": "mytype", "_index": "myindex" } }
{ "name": "doc 3" }
{ "index": { "_type": "mytype", "_index": "myindex" } }
{ "name": "doc 4" }

- POST /{index}/_bulk
{ "index": { "_type": "mytype" } }
{ "name": "doc 5" }
{ "index": { "_type": "mytype" } }
{ "name": "doc 6" }
{ "index": { "_type": "mytype" } }
{ "name": "doc 7" }

- POST /{index}/{type}/_bulk
{ "index": {} }
{ "name": "doc 8" }
{ "index": {} }
{ "name": "doc 9" }
{ "index": {} }
{ "name": "doc 10" }

## Queries
- POST /{index}/_search
- POST /{index}/{type}/_search

Text:
`{
  "query": {
     "match": { "myfield": "myquerytext" }
   }
}`

Range:
`{ 
  "query": {
    "range" : {
      "created_at" : {
        "gte" : "2016-01-08T17:18:12.493-04:00"
      }
    } 
  }
}`

## ID lookups
- GET /{index}/{type}/{_id}

## Counts
 - GET /{index}/_count
 - GET /{index}/{type}/_count

## Utilities/Other
#### _cat
Utility List

- GET /_cat

Universal Parameters

- Verbose: ?v (e.g. GET /_cat/nodes?v)
- Help: ?help (e.g. GET /_cat/indices?help)

Reference: https://www.elastic.co/guide/en/elasticsearch/reference/current/cat.html

#### Cluster State
Cluster Health

- GET /_cluster/health?pretty
- GET /_cat/health?v

## Cheatsheets
http://elasticsearch-cheatsheet.jolicode.com/
