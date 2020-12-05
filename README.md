# Self-Hosted Services #

Acts as a colletion of all self hosted services running on docker.


docker-based plex & usenet media server using custom subdomains with tls

## Motivation

- host each service as a subdomain of a personal domain over https
- run public maintained images with no modifications
- require minimal configuration and setup

## Ports Used
|Port|Service|Description|Public
|---|---|---|---|
|80| Traefik  | HTTP entrypoint  | Y
|443|Traefik|HTTPS entrypoint| Y
|8082|Traefik|Metrics entrypoint| N
|6880| Qbittorrent | WebUI | N
|6881| Qbittorrent| Data Transfer| N
|32400|Plex| LoadBalancer|Y
|32469|Plex| ???|Y
|1900|Plex| ???|Y
|9007| Portainer| WebUI | N
|9191| NextCloud | WebUI | Y
|3579| Ombi | WebUI | Y
|9090| Prometheus| webUI | N
|3000| Grafana | WebUI | N
|9117| Jackett| WebUI| N
|6767| Bazarr| WebUI| N

## Services

### Publicly facing
- [Plex](https://hub.docker.com/r/plexinc/pms-docker) - organizes video, music and photos from personal media libraries and streams them to smart TVs, streaming boxes and mobile devices. This container is packaged as a standalone Plex Media Server.
- [Ombi](https://hub.docker.com/r/linuxserver/ombi/) - Allows you to host your own Plex Request and user management system.
- [Nextcloud](https://hub.docker.com/r/linuxserver/ombi/) - A full-fledged open-source replacement for Google Suite or Microsoft 365. 
### Backend
- [Traefik](https://hub.docker.com/_/traefik/) - a modern HTTP reverse proxy and load balancer that makes deploying microservices easy.
- [qBittorrent](https://hub.docker.com/r/binhex/arch-qbittorrentvpn) - An fast and stable bittorrent client that provides many featurues. This includes in OpenVPN instance based on arch linux that proxies all network requests.  
- [Grafana](https://hub.docker.com/r/grafana/grafana/) - Solution for visualizing analytics & simplifying monitoring. 
- [Prometheus](https://hub.docker.com/r/prom/prometheus/) - Systems monitoring and alerting toolkit. Collects metrics from configured targets at given intervals, evaluates rule expressions, displays the results, and can trigger alerts if some condition is observed to be true
- [Mysql](https://hub.docker.com/_/mysql) - Leading open-source database used for storing metrics
- [MariaDB](https://hub.docker.com/_/mariadb) -Community-developed fork of the MySQL used to store NextCloud Data. 

### Automation
- [Sonarr](https://hub.docker.com/r/linuxserver/sonarr/) - (formerly NZBdrone) is a PVR for usenet and bittorrent users. It can monitor multiple RSS feeds for new episodes of your favorite shows and will grab, sort and rename them. It can also be configured to automatically upgrade the quality of files already downloaded when a better quality format becomes available.
- [Radarr](https://hub.docker.com/r/linuxserver/radarr/) - A fork of Sonarr to work with movies à la Couchpotato.
- [Jackett](smthing) Its Gud.


## Requirements

- dedicated server or PC with plenty of storage
- windows or linux x86/x64 os (not ARM)
- personal top-level domain with configurable sub-domains (eg. plex.mydomain.com)
- domain registered with Cloudflare

## ACME & DNS

The following subdomains should point to the public IP of your server:

- `plex.domain.com`
- `request.domain.com`

Some services are only accessible on LAN

- `traefik.domain.local`
- `grafana.domain.local`
- `prometheus.domain.local`
- `sonarr.domain.local`
- `radarr.domain.local`
- `hydra.domain.local`
- `qbit.domain.local`
  
## Installation

1. install [docker](https://docs.docker.com/install/linux/docker-ce/debian/)

2. install [docker-compose](https://docs.docker.com/compose/install/#install-compose)

3. clone mediaserver repo
```bash
git clone https://github.com/YouFoundKyle/selfhosted.git
```

## Configuration

Copy `env.sample` to `.env` and fill all required fields

```bash
cp env.sample .env && vim .env
```

Note: YOu must run `docker-compose` in same folder as .env

## Deployment

Pull and deploy containers with docker-compose

```bash
docker-compose pull
docker-compose up -d  
```
## CentOS Specific
smthing

## Acknowledgments

This was initially adapted from [Kyle Harding](https://klutchell.dev) and his [MediaServer](https://github.com/klutchell/mediaserver.git) repo
I didn't create any of these docker images myself, so credit goes to the
maintainers, and the original software creators.

- [plex.tv](https://plex.tv/)
- [linuxserver.io](https://linuxserver.io/)
- [traefik.io](https://traefik.io/)

## License  

[MIT License](./LICENSE)
