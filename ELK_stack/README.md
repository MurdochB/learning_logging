This folder contains:

A Dockerfile to make a ELK stack image based off sebp ELK image, along with logstash.conf

To build a new image:
`docker build -t elk:0.1  .`

Run the base version of sebp/elk:551:
`docker run -p 5601:5601 -p 9200:9200 -p 5044:5044 -e "MAX_MAP_COUNT"=262144  -it --name elk3 sebp/elk:551`

Run the extended image of sebp:
`docker run -p 5601:5601 -p 9200:9200 -p 5044:5044 -e "MAX_MAP_COUNT"=262144  -it --name elk1_1 elk_stack:1.1`

run bash in container:
`docker exec -it <container-name> /bin/bash`

Send dummy Log: (run bash in container first)
`/opt/logstash/bin/logstash --path.data /tmp/logstash/data -e 'input { stdin { } } output { elasticsearch { hosts => ["localhost"] } }'`
