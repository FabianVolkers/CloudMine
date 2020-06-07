# CloudMine <!-- omit in TOC -->

A curated collection of Free and Open Source Software to power your own private cloud.

## Contents <!-- omit in TOC -->

- [Services](#services)
  - [Webserver](#webserver)
  - [Autentication & User Management](#autentication--user-management)
  - [Nextcloud](#nextcloud)
  - [Mail](#mail)
  - [Mattermost](#mattermost)
  - [Jitsi](#jitsi)
  - [Monitoring & Logging](#monitoring--logging)
- [Quickstart](#quickstart)
- [Resources](#resources)
- [Powered By](#powered-by)
  - [User facing services](#user-facing-services)
  - [Backbone Services](#backbone-services)

## Services

This is an overview of services which are supported and functional with this Docker setup.

### Webserver
We use Nginx as a reverse proxy to each of the other services. Combined with Let's Encrypt and the Docker-Gen container, this enables automated configuration using solely Environment Variables. Additionally, we run a Nameserver with Dynamic DNS Service using Bind9 and docker-ddns.
More information as well as detailed setup instructions can be found [here](webserver).

### Autentication & User Management
We use OpenLDAP as a user backend. Combined with Ory Hydra and Werther, we also have a working OpenID Connect Service using OAuth 2.0. The Vouch Proxy Service enables us to use the nginx auth_request module to protect any service, regardless of OpenID Connect support.
More information as well as detailed setup instructions can be found [here](authentication).

### Nextcloud
More information as well as detailed setup instructions can be found [here](nextcloud).

### Mail

### Mattermost

### Jitsi

### Monitoring & Logging

## Quickstart

1. Clone this GitHub repository to your VM/VPS/Home Server.
   ```bash
   git clone https://github.com/FabianVolkers/docker-compose.git
   ```
2. Each of the main categories has their own Docker-Compose file. This makes it easier to selectively enable/disable services and modifiy everything to your need. We will start by deploying the webserver project, since all web-facing services rely on nginx to connect to the internet. All environnment variables that need changing are listed in the `example.env` file. Simply replace the example values with your own and rename the file to `.env` configuration that needs to be changed. Afterwards all you have to do is create the `nginx-proxy` network in docker and run `docker-compose up -d`, and you are good to go.
   ```bash
   cd docker-compose/webserver
   cp example.env .env
   sudo docker network create nginx-proxy
   sudo docker-compose up -d
   ```
3. Repeat these steps for each of the services you would like to host. Keep in mind that some of the other services rely on config files to run properly. All required files are present in the repository.

## Resources

https://docs.google.com/document/d/1uG8OLFpA9MtCt-M_BkFxx-WejQnB89aKVtif-tjlils/edit#

## Powered By
### User facing services
<a href="https://grafana.com/"><img src=".github/media/grafana-logo.png" alt-text="grafana-logo" height="100px"/></a>
<a href="https://nextcloud.com/"><img src=".github/media/nextcloud-logo.jpg" alt-text="nextcloud-logo" height="100px"/></a>
### Backbone Services
<a href="https://docker.com/"><img src=".github/media/docker-logo.png" alt-text="docker-logo" height="100px"/></a>
<a href="https://hub.docker.com/_/nginx"><img src=".github/media/nginx-logo.png" alt-text="nginx-logo" height="100px"/></a>
<a href="https://github.com/nginx-proxy/docker-letsencrypt-nginx-proxy-companion"><img src=".github/media/lets-encrypt-logo.png" alt-text="letsencrypt-logo" height="100px"/></a>
<a href="https://github.com/dprandzioch/docker-ddns"><img src=".github/media/bind-9-logo.jpg" alt-text="bind9-logo" height="100px"/></a>
<a href="https://github.com/osixia/docker-openldap"><img src=".github/media/openldap-logo.png" alt-text="openldap-logo" height="100px"/></a>
<a href="https://github.com/osixia/docker-phpLDAPadmin"><img src=".github/media/phpldapadmin-logo.jpg" alt-text="php-ldap-admin-logo" height="100px"/></a>
<a href="https://www.ory.sh/hydra/"><img src=".github/media/ory-logo.png" alt-text="ory-logo" height="100px"/></a>
<a href="https://github.com/vouch/vouch-proxy"><img src=".github/media/vouch-logo.png" alt-text="vouch-logo" height="100px"/></a>
<a href="https://prometheus.io/"><img src=".github/media/prometheus-logo.png" alt-text="prometheus-logo" height="100px"/></a>
<a href="https://www.elastic.co/elastic-stack"><img src=".github/media/elk-stack-logo.png" alt-text="elastic-stack-logo" height="100px"/></a>

- https://github.com/jwilder/docker-gen
- https://github.com/i-core/werther
- https://github.com/pulsejet/nextcloud-oidc-login