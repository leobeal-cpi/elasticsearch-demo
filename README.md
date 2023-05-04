# Elasticsearch Demo
This is a simple Elasticsearch demo.
It contains basic instructions on how to create an index, insert data and query it.

## Clone this repository
```bash
git clone git@github.com:leobeal-cpi/elasticsearch-demo.git
```
## How to start
### Start your containers
```bash
docker-compose up -d
```

### Check that ES is running
```bash
curl -XGET http://localhost:9200
```

or open http://localhost:9200 in your browser

## Create index
```bash
curl -XPUT http://localhost:9200/stations -H 'Content-Type: application/json' -d @examples/index_mapping.json
```
This will create an index named `stations` with the mapping defined in `examples/index_mapping.json`.

If you want to remove the index recently created simply run `curl -XDELETE http://localhost:9200/stations`

## Check that the index was created
```bash
curl -XGET http://localhost:9200/_cat/indices
```

## Inserting data
```bash
curl -XPOST http://localhost:9200/stations/_doc -H 'Content-Type: application/json' -d @examples/station_data.json
```

## Querying data
```bash
curl -XGET http://localhost:9200/stations/_search?pretty -H 'Content-Type: application/json' -d @examples/query.json
```

Check https://www.elastic.co/guide/en/elasticsearch/reference/current/geo-queries.html for more information on geo queries.
