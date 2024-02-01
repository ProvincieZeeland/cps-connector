# CPS-connector
The CPS-connector is set of Docker containers used for updating our Elasticsearch nodes using API requests with optional notification to external parties (websites, DIWOO sitemaps) as well as importing data from external sources. 
My first Python project after 23 years using PHP code :-).

This repository contains the Python based API / workers, used applications at https://github.com/ProvincieZeeland/cps-connector-applications

## Versions
If you're interested in versions (which are no longer available), have a look at (https://github.com/ProvincieZeeland/cps-connector/wiki/Version-history)

## Getting started
When all neede applications are up and running (without the NGINX proxy) you need to create some networks (docker network create <name>:

- cps_acc
- cps_prod
- docker_proxy
- redis
- rabbit



- [Elasticsearch](https://github.com/ProvincieZeeland/cps-connector/tree/elasticsearch)
 
## Getting started

- [1: Configure Elasticsearch / Kibana](https://github.com/ProvincieZeeland/es-connector/wiki/1:-Configure-Elasticsearch--&-Kibana-nodes)
- [2: Setup Elasticsearch mappings etc.](https://github.com/ProvincieZeeland/es-connector/wiki/2:-Setup-Elasticsearch-mappings-etc.)
- [3: Configure the API](https://github.com/ProvincieZeeland/es-connector/wiki/3:-Configure-the-API)
- [4: Firing up the proxy](https://github.com/ProvincieZeeland/es-connector/wiki/4:-Firing-up-the-proxy)

