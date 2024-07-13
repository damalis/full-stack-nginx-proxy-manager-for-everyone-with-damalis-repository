# [full stack Nginx Proxy Manager for everyone with damalis repository](https://github.com/damalis/full-stack-nginx-proxy-manager-for-everyone-with-damalis-repository)

If You want to build a website with Nginx Proxy Manager at short time;

#### Full stack Nginx Proxy Manager:
<p align="left"> <a href="https://https://nginxproxymanager.com/" target="_blank" rel="noreferrer"> <img src="https://avatars.githubusercontent.com/u/88089605?s=200&v=4" alt="nginx proxy manager" height="40" width="40"/> </a>&nbsp;&nbsp;&nbsp; 
<a href="https://github.com/damalis?tab=repositories" target="_blank" rel="noreferrer"> <img src="https://avatars.githubusercontent.com/u/11361779?v=4" alt="damalis" width="40" height="40" width="40"/> </a>&nbsp;&nbsp;&nbsp;</p>

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

    wordpress:
    .
    .
    .
```

then

continue damalis repository guide

### Nginx Proxy Manager Admin

```http://example.com:81``` Attention: http without "s".

#### Default Administrator User

```
Email:    admin@example.com\
Password: changeme
```