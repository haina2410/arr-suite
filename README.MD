# Docker Compose Media Server Suite
This repository contains a Docker Compose configuration for setting up a comprehensive media server suite on a Linux machine. The setup includes various applications for downloading, managing, and streaming media content.

### Services Included
- WireGuard: Secure VPN tunnel for routing all traffic through a VPN.
- qBittorrent: High-performance BitTorrent client for downloading files.
- Prowlarr: Indexer manager that integrates with your downloading and media software.
- Sonarr: Automatic TV series management and organizer.
- Radarr: Movie collection manager and organizer.
- Jellyfin: Media server for streaming your media to various devices.
- Bazarr: Manages and downloads subtitles for your media library.

### Network Configuration
All services are connected through a custom Docker network wireguard_net with a specified subnet. This network ensures isolation and efficient communication between services.

### Volume Management
Persistent storage is configured using Docker volumes and bind mounts:
- Configuration files are stored in the configs directory.
- Media content directories are mapped to external storage paths.
- Ensure that the specified directories exist and have appropriate permissions.

### Setup Instructions
1. Prerequisites: Install Docker and Docker Compose on your Linux machine.
2. Clone Repository: Clone this repository to your local machine.
3. Configuration: Review and modify the docker-compose.yml file to suit your environment.
  - Update environment variables like PUID, PGID, and TZ.
  - Adjust volume paths to point to your media directories.
4. Starting Services: Run `docker-compose up -d` to start all services in detached mode.
5. Accessing Applications: Access each application through the mapped ports:
  - qBittorrent: http://localhost:8180
  - Sonarr: http://localhost:8989
  - Radarr: http://localhost:7878
  - Jellyfin: http://localhost:8096
  - Bazarr: http://localhost:6767
  - Prowlarr: http://localhost:9696

### Notes
- WireGuard Dependency: The WireGuard service must be running before dependent services start.
- Permissions: Ensure the user IDs (PUID and PGID) match your system user for proper permissions.
- Restart Policies: Most services are set to restart automatically for stability.
- Support: For detailed configurations and advanced setups, refer to the official documentation of each service. If you encounter issues, please check the logs of individual containers for troubleshooting.