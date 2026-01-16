Sudo docker ps
// to check docker container
// it will show container id that will be used in next command

sudo docker inspect c5095d77eb20
// to show docker network configuration

sudo docker inspect network bridge

sudo docker exec -it DC_EnterpriseAgent_CDC bash
// takes you into your container bash
hostname
hostname -I


sudo docker image ls
// shows docker image installed

Sudo docker version
// to check docker version


sudo docker compose version
// to check docker compose version

Instead of docker-compose command, use sudo /bin/docker compose
//because we have not created the alias
sudo /bin/docker compose


To get into bash:
sudo docker run --rm -it -v /app:/app --name ol8 oraclelinux:8-slim /bin/bash

To get into bash:
sudo docker exec -it 3cd29827dae3 bash.    //container id



Index Lifecycle:

1- Index Lifecycle Policy
Create ILM named kibana-reporting

2- Index template
Associate ILM with Index Template

{
  "index": {
    "lifecycle": {
      "name": "kibana-reporting",
      "rollover_alias": "elogs"
    },
    "mapping": {
      "total_fields": {
        "limit": "10000"
      }
    },
    "refresh_interval": "5s"
  }
}

3- Indices
Logstash pipeline config - 
output {
        elasticsearch {
                hosts => "elasticsearch:9200"
                ilm_rollover_alias => "elogs"
                ilm_pattern => "{now/d}-000001"
                ilm_policy => "kibana-reporting"
                


Indexing:
https://www.youtube.com/watch?v=2WJFMYAri_8


             

Go to the directory of syslog-ng docker compose file, if you want to build new container

sudo /bin/docker compose down
sudo /bin/docker compose up -d --build

--build builds new container. 
Without --build, you will be restarting the container


Elastic Search Cluster


To find which node is Master

curl 'localhost:9200/_cat/master?v'


// bootstraping Elastic Search index (only need to do it initially)
// ---------------------
PUT elogs-000001
{
  "aliases": {
    "elogs": {
      "is_write_index": true
    }
  }
}

// ---------------


