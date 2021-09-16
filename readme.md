## Why Kong?
* Trying out the API Management capabilities more than as Ingress where i often use Traefik.
* Can run completely standalone from central/cloud services
* Built on NGINX and implemented as a LUA
* There is ALOT of plugins!
* Kong is a mature and popular API-management platform
* The Kong gateway is completely open source and free
* Does not need Kong Konnect 

## TEST
* Simple test using docker and a declarative kong configuration file 
* Only port 8000 need to be exposed via ingress. Kong Admin-ports are not needed when doing 100% static and declarative config.

## DOCKER manually without docker-compose
docker run --rm --name kong -e "KONG_DATABASE=off" -e "KONG_PROXY_ACCESS_LOG=/dev/stdout" -e "KONG_ADMIN_ACCESS_LOG=/dev/stdout" -e "KONG_PROXY_ERROR_LOG=/dev/stderr" -e "KONG_ADMIN_ERROR_LOG=/dev/stderr" -e "KONG_ADMIN_LISTEN=0.0.0.0:8001, 0.0.0.0:8444 ssl" -e "KONG_DECLARATIVE_CONFIG=/home/kong/kong.yml" -e "KONG_HEADERS=off" -p 8000:8000 -p 8443:8443 -p 8001:8001 -p 8444:8444 -v ./kong.yml:/home/kong/kong.yml kong

To use docker-compose see file in this repo
