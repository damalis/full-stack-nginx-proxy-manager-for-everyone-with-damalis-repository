# [full stack Nginx Proxy Manager for everyone with damalis repository](https://github.com/damalis/full-stack-nginx-proxy-manager-for-everyone-with-damalis-repository)

If You want to build a website with Nginx Proxy Manager at short time;

#### Full stack Nginx Proxy Manager:
[![Nginx Proxy Manager](https://img.shields.io/badge/Nginx%20Proxy%20Manager-009639?style=flat)](https://https://nginxproxymanager.com/)
[![Damalis GitHub Repositories](https://img.shields.io/badge/Damalis-Repositories-181717?style=flat&logo=github)](https://github.com/damalis?tab=repositories)

#### IPv4/IPv6 Firewall

Create rule to open port to the internet, or to a specific IPv4 address or range.

- http: 81

### How to 
add "npm.yml" file code in "docker-compose.yml" file

#### Example

```
services:

    npm:
        depends_on:
            certbot:
                condition: service_healthy
        image: jc21/nginx-proxy-manager:latest
        container_name: npm
        networks:
            - backend
            - frontend
        volumes:
            - ./npm:/data
            - 'certbot-etc:${LETSENCRYPT_CONF_PREFIX}'
        hostname: npm
        restart: unless-stopped
        ports:
            - '81:81' # Admin Web Port
            # Add any other Stream port you want to expose
            # - '21:21' # FTP
        links:
            - database
        environment:
            # Uncomment this if you want to change the location of
            # the SQLite DB file within the container
            # DB_SQLITE_FILE: '/data/database.sqlite'
            TZ: '${LOCAL_TIMEZONE}'
            # Uncomment this if IPv6 is not enabled on your host
            # DISABLE_IPV6: 'true'

    webserver:
    .
    .
    .
```

then

continue damalis repository guide

#### Log in to the Admin UI

```http://DOMAIN_NAME:81``` Attention: http without "s".

#### Default Admin User

```
Email:    admin@DOMAIN_NAME
Password: changeme
```

Immediately after logging in with this default user you will be asked to modify your details and change your password.