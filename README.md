# cps-connector
The CPS-connector is set of Docker containers used for updating our Elasticsearch nodes using API requests with optional notification to external parties (websites, DIWOO sitemaps) as well as importing data from external sources. 
My first Python project after 23 years using PHP code :-) 
 
## Version history

### 0.1 Proof of Concept
The PoC is a fully functional but pretty basic solution which supports:

- Different environments (development, accept, production) using .env / Docker compose files.
- Authentication based on Bearer tokens using decorators.
- Receive and validate posted JSON data and map it to an Elasticsearch structure.
- Add, update and delete mapped metadata in Elasticsearch.
- If referred content is a PDF file; get PDF from Sharepoint storage, extract text and add to metadata for full text searches.
- Notify external parties about the change (webhook).
- Serve metadata (JSON format) and content (eg PDF) format upon request.

### 0.2 Small optimizations

- Python Docker image replaced with one with less vulnerabilities (python:3.10-7-slim-buster -> python:3.12-rc-slim).
- Removed CADDY for local development, only nginx now.
- Enabled logrotation for Docker daemon / Docker Containers.
- Added healthchecks for API containers and nginx.
- Redefined the Elastic mapping to a more flat version / updated Python code.
- Added new mapping / Python code for saving transaction data and timing (request, workflows and responses).
- Elastic related operations are now devided into 2 Docker containers (1 for read, 1 for write aka CQRS).

### 0.6 Pretty much a rewrite

- Read actions (metadata / content) is now a separate container.
- Update actions are now queued using RabbitMQ and handled by a dedicated Python worker.
- PHP based Dashboard for ACC / PROD environment with option to view transaction metadata.
- Docker proxy container to access Docker API (dashboard).
- Tokens are now more complex and authentication now handled by a dedicated Docker container (Enigma).
- All containers now use correct timezone (Amsterdam).
- All containers now have a mount to a local path for logfiles.
- Set container security
- Some performance changes for Elasticsearch.
- Added support for updating XML sitemaps for DIWOO.
- Importing data / documents based on Zaaksysteem webhook with version control / oAUTH authentication (redis).
- Uptime / resource monitoring using Uptime-Kuma.

**TODO**

- Swagger / OpenAPI specs.
- Search endpoint

## Architecture overview
**CPS EXPORT**
![cps-export](https://github.com/ProvincieZeeland/cps-connector/assets/196572/79665788-cf78-405b-b8f6-78bbf65905b6)

**CPS IMPORT (zaaksysteem)**
**CP![zaaksysteem](https://github.com/ProvincieZeeland/cps-connector/assets/196572/36701594-b1ba-4e2b-b5a4-9467ef6cae78)

## Getting started
After cloning this repo, you should have a map structure like this:

```
|-- Info.md
|-- api
|-- elasticsearch
|-- proxy
```
 
- [1: Configure Elasticsearch / Kibana](https://github.com/ProvincieZeeland/es-connector/wiki/1:-Configure-Elasticsearch--&-Kibana-nodes)
- [2: Setup Elasticsearch mappings etc.](https://github.com/ProvincieZeeland/es-connector/wiki/2:-Setup-Elasticsearch-mappings-etc.)
- [3: Configure the API](https://github.com/ProvincieZeeland/es-connector/wiki/3:-Configure-the-API)
- [4: Firing up the proxy](https://github.com/ProvincieZeeland/es-connector/wiki/4:-Firing-up-the-proxy)

