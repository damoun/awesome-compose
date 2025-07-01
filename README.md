<img align="left" width="0" height="192px" hspace="10"/>
<h1 align="center">
  <br><img src="project-logo.jpeg">
  <br>
  awesome-compose
  <br>
</h1>

<h4 align="center">A curated collection of Docker Compose configurations for popular applications and services.</h4>

<p align="center">
  <a href="https://awesome.re"><img src="https://awesome.re/badge.svg" alt="awesome-badge"></a>
  <a href="LICENSE"><img src="https://img.shields.io/github/license/damoun/awesome-compose.svg" alt="license-badge"></a>
</p>

<p align="center">
  <a href="#samples">Samples</a> •
  <a href="#getting-started">Getting Started</a> •
  <a href="#troubleshooting">Troubleshooting</a>
</p>

## Samples

- [`Prometheus / Blackbox Exporter`](prometheus-blackbox) - Complete monitoring setup with Prometheus and Blackbox Exporter for endpoint monitoring and health checks

<!-- 
Future samples to be added:
### Databases
### Web Servers & Reverse Proxies  
### Development Tools
### CI/CD Tools
### Message Queues
### Caching Solutions
-->

## Getting started

These instructions will guide you through setting up and deploying containerized applications using the Docker Compose samples in this repository.

### Prerequisites

- **Docker & Docker Compose**: Make sure you have both installed on your system
  - **Windows or macOS**: [Install Docker Desktop](https://www.docker.com/get-started) (includes Docker Compose)
  - **Linux**: Install [Docker](https://docs.docker.com/engine/install/) and [Docker Compose](https://docs.docker.com/compose/install/)
- **Git**: To clone this repository
- **Basic terminal/command line knowledge**

### Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/damoun/awesome-compose.git
   cd awesome-compose
   ```

2. **Choose a sample**: Browse the available samples and navigate to the one you want to try

### Running a sample

Each sample is contained in its own directory with a `compose.yaml` file that describes the service configuration.

1. **Navigate to the sample directory**:
   ```bash
   cd <sample-name>
   ```

2. **Start the services**:
   ```bash
   docker compose up -d
   ```
   
   The `-d` flag runs containers in detached mode (in the background).

3. **Check the services are running**:
   ```bash
   docker compose ps
   ```

4. **View logs** (optional):
   ```bash
   docker compose logs -f
   ```

### Stopping a sample

To stop and remove all containers of a sample:

```bash
docker compose down
```

To also remove volumes (⚠️ **this will delete all data**):

```bash
docker compose down -v
```

## Troubleshooting

### Common Issues

**Port conflicts**: If you get port binding errors, check if the ports are already in use:
```bash
# Check what's using a specific port (replace 8080 with your port)
lsof -i :8080
```

**Permission issues**: On Linux, you might need to add your user to the docker group:
```bash
sudo usermod -aG docker $USER
# Log out and back in for changes to take effect
```

**Container startup failures**: Check the logs for detailed error messages:
```bash
docker compose logs <service-name>
```

**Docker VM disk space full (macOS)**: If you run out of disk space, Docker may fail to start containers or pull images. Free up space by removing unused data:

```bash
docker system prune -a
```

This command deletes all stopped containers, unused networks, dangling images, and optionally, unused volumes. Review what will be deleted before confirming.
