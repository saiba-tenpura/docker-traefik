# Docker Traefik
A Traefik docker compose instance for usage in other compose setups as reverse proxy.

## Setup the network
```
docker network create \
  --driver=bridge \
  --attachable \
  --internal=false \
  proxy-network
```

## Usage
To use it in a compose setup make the following adjustments to the service which should be proxied.
```
# compose.yaml
services:
  service:
    ...
    networks:
      ...
      - proxy-network
    ...
    labels:
      - "traefik.enable=true"
      - "traefik.http.routers.<SERVICE>.rule=Host(`${SERVICE_DOMAIN}`)"

networks:
  ...
  proxy-network:
    external: true
```

## Other Repositories
The following repositores are intended to be used with this setup and are implementing the aforementioned usage:
- [Authentik](https://github.com/saiba-tenpura/docker-authentik) - Identity provider for SSO.
- [Booklore](https://github.com/saiba-tenpura/docker-booklore) - Digital library.
- [Kaneo](https://github.com/saiba-tenpura/docker-kaneo) - Project management platform.
- [Nebula Sync](https://github.com/saiba-tenpura/docker-nebula-sync) - Pi-hole synchronization.
- [Static Nginx](https://github.com/saiba-tenpura/docker-nginx-static) - A basic nginx setup for serving static content.
- [Paperless](https://github.com/saiba-tenpura/docker-paperless) - Document managemend system.
- [Pi-hole](https://github.com/saiba-tenpura/docker-pi-hole) - DNS sinkhole incl. unbound as upstream DNS.

## License
[MIT](./LICENSE)
