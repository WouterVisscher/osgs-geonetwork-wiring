# osgs-geonetwork-wiring

## steps

1. Start OSGS
1. Start GeoNetwork
1. Connect network
1. Config NGINX

## Start OSGS

See the Makefile and kartoza/osgs documentation

## Start GeoNetwork

See the Saint Lucia geonetwork/docker-geonetwork/4.2.3
docker-compose-stlucia.yaml file

## Connect network

Now the NGINX in the OSGS stack needs to be wired into the docker network of
GeoNetwork

```bash
docker network connect 423_gn-network osgs-geonetwork-wiring_nginx_1
```

## Connect NGINX

A NGINX configuration needs to be added to the NGINX in the OSGS stack. This can
be done by copying (or creating):

* the geonetwork.conf.available into the mounted conf/nginx_conf/locations.
* create a symbolic link `ln -s geonetwork.conf.available geonetwork.conf`
* restart the OSGS NGINX

```bash
docker restart osgs-geonetwork-wiring_nginx_1
```
