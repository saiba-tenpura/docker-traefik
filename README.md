# Docker Traefik
A Traefik docker compose instance for usage in other compose setups as reverse proxy.

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
| Project                                                              | Description                                             |
| -------------------------------------------------------------------- | ------------------------------------------------------- |
| [Authentik](https://github.com/saiba-tenpura/docker-authentik)       | Identity provider for SSO.                              |
| [Gitea](https://github.com/saiba-tenpura/docker-gitea)               | DevOps and Git repository management platform.          |
| [Headscale](https://github.com/saiba-tenpura/docker-headscale)       | Self-hosted mesh VPN control server build on WireGuard. |
| [Kaneo](https://github.com/saiba-tenpura/docker-kaneo)               | Project management platform.                            |
| [Kavita](https://github.com/saiba-tenpura/docker-kavita)             | Digital library.                                        |
| [Monitoring](https://github.com/saiba-tenpura/docker-monitoring)     | Monitoring setup build around Prometheus & Grafana.     |
| [Nebula Sync](https://github.com/saiba-tenpura/docker-nebula-sync)   | Pi-hole synchronization.                                |
| [Pi-hole](https://github.com/saiba-tenpura/docker-pi-hole)           | DNS sinkhole incl. unbound as upstream DNS.             |
| [Radicale](https://github.com/saiba-tenpura/docker-radicale)         | CalDAV (calendars) & CardDAV (contacts) server.         |
| [Static Nginx](https://github.com/saiba-tenpura/docker-nginx-static) | A basic nginx setup for serving static content.         |

## License
[MIT](./LICENSE)
