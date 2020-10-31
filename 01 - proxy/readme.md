### Config for traefik
# Network
Add this network to aevery services you want to be accessible through the proxy
```
docker network create \
  --attachable \
  --driver=overlay \
proxy
```
# Environement
Create an env files with the following variables
```
OVH_ENDPOINT=<ovh-eu or ovh-ca>
OVH_APPLICATION_KEY=<application-key>
OVH_APPLICATION_SECRET=<application-secret>
OVH_CONSUMER_KEY=<consumer-key>
```
ovh_api.env
