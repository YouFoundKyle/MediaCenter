# Docker Plex & Usenet Media Server #

Acts as a colletion of all self hosted services running on docker.


docker-based plex & usenet media server using custom subdomains with tls

## Motivation

- host each service as a subdomain of a personal domain over https
- run public maintained images with no modifications
- require minimal configuration and setup

## All Ports

Traefik
    EntryPoints:
        http = ":80"
        https = ":443"
        metrics = ":8082"
Qbittorrent
    WebUI = 6880
    Data = 6881
Plex
    Loadbalancer  = 32400 NAt 8752

    ??? = 32469
    ??? = 1900
Nextcloud
    WebUI = 9191
Ombi
    WebUI = 3579
Prometheus
    webUI  = 9090
Grafana
    webUI  = 3000
Jackett
    webUI  = 9117

## Services

### User faceing
- [Plex](https://hub.docker.com/r/plexinc/pms-docker) - organizes video, music and photos from personal media libraries and streams them to smart TVs, streaming boxes and mobile devices. This container is packaged as a standalone Plex Media Server.
- [qBitorrent](https://hub.docker.com/r/binhex/arch-qbittorrentvpn) - something something something. Includes in OpenVPN instance and built on arch linux
- [Ombi](https://hub.docker.com/r/linuxserver/ombi/) - Meant for users to request media.
- [Nextcloud](https://hub.docker.com/r/linuxserver/ombi/) - stores data.
### Backend
- [Traefik](https://hub.docker.com/_/traefik/) - a modern HTTP reverse proxy and load balancer that makes deploying microservices easy.
- [Grafana](https://hub.docker.com/_/traefik/) - visualize metrics.
- [Prometheus](https://hub.docker.com/_/traefik/) - pull metrics.
- [Mysql](smthing) - stores metrics
- [MariaDB](smthing) - stores nextcloud data  

### Automation
- [Sonarr](https://hub.docker.com/r/linuxserver/sonarr/) - (formerly NZBdrone) is a PVR for usenet and bittorrent users. It can monitor multiple RSS feeds for new episodes of your favorite shows and will grab, sort and rename them. It can also be configured to automatically upgrade the quality of files already downloaded when a better quality format becomes available.
- [Radarr](https://hub.docker.com/r/linuxserver/radarr/) - A fork of Sonarr to work with movies à la Couchpotato.
<!-- - [NZBHydra](https://hub.docker.com/r/linuxserver/hydra2/) 2 is a meta search application for NZB indexers, the "spiritual successor" to NZBmegasearcH, and an evolution of the original application NZBHydra . It provides easy access to a number of raw and newznab based indexers. -->


## Requirements

- dedicated server or PC with plenty of storage
- windows or linux x86/x64 os (not ARM)
- personal top-level domain with configurable sub-domains (eg. plex.mydomain.com)
- domain registered with Cloudflare

## ACME & DNS

The following subdomains should point to the public IP of your server:

- `plex.domain.com`
- `traefik.domain.com`
- `request.domain.com`

Some services are only accesible on LAN

- `grafana.domain.local`
- `prometheus.domain.local`
- `sonarr.domain.local`
- `radarr.domain.local`
- `hydra.domain.local`

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

Must Run docker compose command in same folder as .env
## Deployment
 Create a user called  

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
