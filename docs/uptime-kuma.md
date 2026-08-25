# Uptime Kuma

Uptime Kuma is the first application deployed in this homelab.

## Purpose

Uptime Kuma is being used to monitor the availability of services and infrastructure within the homelab.

## Deployment

Uptime Kuma is deployed as a Docker container using Docker Compose.

### Docker Image

louislam/uptime-kuma:2

### Container

uptime-kuma

### Restart Policy

The container uses:

restart: unless-stopped

This allows Docker to automatically restart the container after a server or Docker Engine restart, unless the container was intentionally stopped.

## Network

Docker Compose automatically created a dedicated network for this application:

uptime-kuma_default

## Port

Uptime Kuma uses port 3001.

The port mapping is:

Host:3001 → Container:3001

The web interface can be accessed through:

http://<server-ip>:3001

## Persistent Data

The application data is stored outside the container on the Ubuntu host.

Host path:

/opt/homelab/data/uptime-kuma

Container path:

/app/data

The bind mount is configured as:

/opt/homelab/data/uptime-kuma:/app/data

This allows the application data to persist even if the container is removed and recreated.

## Docker Concepts Practiced

This deployment introduced the following Docker concepts:

- Docker Images
- Docker Containers
- Docker Compose
- Compose files
- Port mapping
- Bind mounts
- Persistent data
- Docker Networks
- Restart policies
- Container health status

## Current Status

Status: Running

First deployed: August 2026

## Lessons Learned

This was the first real application deployed in the homelab.

The deployment helped establish the distinction between:

- Image — the packaged application used to create containers.
- Container — a running instance created from an image.
- Compose file — a declarative description of how the application should be deployed.
- Persistent data — application data stored outside the container.
- Docker Network — the network used by containers to communicate.

## Configuration

The Docker Compose configuration for this service is available at:

apps/uptime-kuma/compose.yaml

## Future Improvements

Possible future improvements include:

- Add additional services to Uptime Kuma for monitoring.
- Monitor the Docker host itself.
- Add notification channels.
- Integrate Uptime Kuma with other monitoring and alerting tools.
- Document backup and recovery procedures.
