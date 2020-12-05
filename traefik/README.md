# Traefik
Traefik is an open-source Edge Router that handles network access to docker services. It essentially takes inbound requests and directs them to the proper service.

## Middlewares
---
Middlewares serve as a way to interact with and change HTTP requests before they reach a service. There are various middleware schemes currently in use. 

### Basic Auth
The `basicauth` middleware serves as a way to add simple username/password authentication to a service

### IPwhitelist
The `ipwhitelist` middleware allows requests to be dropped if they don't come from an approved IP address range

### Redirect Scheme
The `redirectscheme` middleware allows requests from one router to be redirected to another. In this case, `http` requests are always redirected to `https`.  

### Secure Headers
The `secureheaders` middleware adds various headers to requests moving through Trafik with the intent of increasing security standards.

## Additional Information
----
The official Traefik documentation can be found [here](https://doc.traefik.io/traefik/)