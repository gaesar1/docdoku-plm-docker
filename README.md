# DocDokuPLM Docker

Easy setup for DocDokuPLM with docker-compose.

## Prerequisites

* [Docker](https://docs.docker.com/get-docker/)
* [Docker Compose](https://docs.docker.com/compose/install/)
* [Set vm.max_map_count to at least 262144](https://www.elastic.co/guide/en/elasticsearch/reference/current/docker.html#_set_vm_max_map_count_to_at_least_262144)

## Start DocDokuPLM:

Clone or [download](https://github.com/docdoku/docdoku-plm-docker/archive/master.zip) this repository.

```
$ git clone https://github.com/docdoku/docdoku-plm-docker.git
$ cd docdoku-plm-docker
```

Open a terminal and run

```
$ ./start.sh
```

You can now verify that all containers are up

```
$ docker-compose ps
```

Then you can access to http://localhost:8000 from your web browser

## Default port mapping

```
--------------------------
Port    Service
--------------------------
8000    docdoku-plm-front
8001    docdoku-plm-server
8002    kibana
8003    mailhog
8004    adminer
--------------------------
```

## SSL support (optional)

You can get HTTPS on your localhost working out of the box.

Create a new entry in /etc/hosts. Note: after editing this file you might have to restart your networking service depending on your OS.

```
127.0.0.1 docdokuplm.local
```

Import the [rootCA](./proxy/ssl/rootCA.pem) sslcertificate to your browser trusted authorities.

Then you can access to https://docdokuplm.local:9000 from your web browser

## Running in production

Make sure to edit all passwords in env files before you start the script. Please also consider using a firewall and remove any unnecessary port mapping from docker-compose.yml.