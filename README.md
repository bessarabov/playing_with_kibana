# Just playing with kibana

Start:

    docker-compose build ; docker-compose up -d

Stop:

    docker-compose stop ; docker-compose rm --force

## Introduction video

https://www.elastic.co/webinars/introduction-elk-stack

## Tutorial

https://www.elastic.co/guide/en/kibana/3.0/import-some-data.html


    curl -XPUT http://docker:9200/shakespeare -d '
    {
     "mappings" : {
      "_default_" : {
       "properties" : {
        "speaker" : {"type": "string", "index" : "not_analyzed" },
        "play_name" : {"type": "string", "index" : "not_analyzed" },
        "line_id" : { "type" : "integer" },
        "speech_number" : { "type" : "integer" }
       }
      }
     }
    }
    ';


    curl -XPUT docker:9200/_bulk --data-binary @shakespeare.json
