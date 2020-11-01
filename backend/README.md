# qBittorrent

This is a docker container built with arch 
## Variables

Variable | Description
--------- | -------
PUID						|	UID of the user this container will run as  
PGID						|	GID of the user this container will run as
LAN_NETWORK					|	The IP subnet of the LAN. Ex: 192.168.1.0/24
VPN_ENABLED					|	Enable openVPN on container startup
VPN_PROV					|	the VPN provider that will be used with openVPN
VPN_USER					|	username for VPN_PROV credentials 
VPN_PASS					|	password for VPN_PROV credentials
WEBUI_PORT					|	Port that the webUI will be accessible on
NAME_SERVERS				|	'${NAME_SERVERS}'
STRICT_PORT_FORWARD			|	'no'
ENABLE_PRIVOXY				|	Enable Privoxy on container startup
DEBUG						|	Enable debug information to be logged 
## Configuration



1. Change default user/pass
   
### OpenVPN Setup

1. Setup proxy using PIA
Generate OpenVPN config 
Put it in config folder


Go to [PIA's openVPN config generator](https://www.privateinternetaccess.com/pages/ovpn-config-generator). 

Head to $(CONFIG_DIR)/qbittorrent/config/openVPN
Generate the proper OpenVPN
put it in the qbitorrent config/openvpn folder 
    only put one in there


### Slack Notification Setup

1. Navigate to Settings --> Connections --> Slack
2. Use the Same webhook as Watchtoer
3. Select specified Vars
    1. Recommended
        - Username - "TV Shows"
        - Icon - https://github.com/Sonarr/Sonarr/raw/phantom-develop/Logo/128.png
        - Channel - 'tv show'