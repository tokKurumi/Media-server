# Media Server Stack with Docker & *arr Applications

This repository provides a complete media server stack using Docker Compose, featuring the popular *arr suite and supporting applications for automated media management, downloading, and streaming.

## Features

- **VPN Protection**: All downloads are routed through a VPN using [Gluetun](https://github.com/qdm12/gluetun).
- **Torrent Client**: [qBittorrent](https://github.com/linuxserver/docker-qbittorrent) for efficient torrenting.
- **Indexer Management**: [Prowlarr](https://github.com/linuxserver/docker-prowlarr) for managing indexers.
- **Media Managers**:
    - [Sonarr](https://github.com/linuxserver/docker-sonarr) (TV)
    - [Radarr](https://github.com/linuxserver/docker-radarr) (Movies)
    - [Lidarr](https://github.com/linuxserver/docker-lidarr) (Music)
    - [Readarr](https://github.com/linuxserver/docker-readarr) (Books)
- **Media Processing**: [FileFlows](https://fileflows.com/) for automated file organization and processing.
- **Media Server**: [Jellyfin](https://github.com/linuxserver/docker-jellyfin) for streaming your media library.
- **Media Requests**: [Jellyseerr](https://github.com/Fallenbagel/jellyseerr) for managing user requests.

## Stack Overview

| Service      | Port(s)          | Purpose                        |
|--------------|------------------|--------------------------------|
| Gluetun      | Custom from QBIT | VPN gateway                    |
| qBittorrent  | Custom           | Torrent client (via VPN)       |
| Prowlarr     | 9696             | Indexer management             |
| Sonarr       | 8989             | TV series management           |
| Radarr       | 7878             | Movie management               |
| Lidarr       | 8686             | Music management               |
| Readarr      | 8787             | Book management                |
| FileFlows    | 19200            | Media file processing          |
| Jellyfin     | 8096             | Media streaming server         |
| Jellyseerr   | 5055             | Media request management       |

## Usage

1. **Clone this repository** and copy the example environment file:
     ```sh
     cp .env.example .env
     ```
2. **Edit `.env`** with your configuration (VPN, ports, directories, etc.).
3. **Start the stack**:
     ```sh
     docker compose up -d
     ```
4. Access each service via their respective ports.

## Requirements

- Docker & Docker Compose
- NVIDIA GPU (optional, for hardware acceleration in Jellyfin/FileFlows)

## Notes

- All services are configured to use a shared `media_network` for easy communication.
- qBittorrent runs behind Gluetun for privacy.
- Hardware acceleration is enabled for Jellyfin and FileFlows if an NVIDIA GPU is present.

## Credits

- [LinuxServer.io](https://www.linuxserver.io/) for most Docker images.
- [*arr Community](https://wiki.servarr.com/) for automation tools.

---

**Enjoy your automated media server!**