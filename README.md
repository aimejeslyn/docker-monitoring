

# System Monitoring

This repository contains a setup for monitoring an IPFS (InterPlanetary File System) node using Prometheus, Grafana, and Node Exporter.

## Overview

This monitoring setup utilizes the following components:

- **Prometheus**: A monitoring and alerting toolkit designed for reliability and scalability.
- **Grafana**: A multi-platform open-source analytics and interactive visualization web application.
- **Node Exporter**: A Prometheus exporter for hardware and OS metrics exposed by Unix kernels.
- **IPFS Metrics**: Metrics scraping configured to collect metrics from IPFS nodes for monitoring and analysis.

## Docker Compose Configuration

The `docker-compose.yml` file defines the services and their configurations:

### Prometheus Service

- **Image:** `bitnami/prometheus:latest`
- **Ports:** Exposed on port `9090`
- **Volumes:** Mounts `./prometheus.yml` from the host to `/etc/prometheus/prometheus.yml` in the container
- **Command:** Specifies the Prometheus configuration file using `--config.file=/etc/prometheus/prometheus.yml`
- **Without Command:**  Change volumes to './prometheus.yml:/opt/bitnami/prometheus/conf/prometheus.yml'

### Grafana Service

- **Image:** `grafana/grafana:latest`
- **Ports:** Exposed on port `3000`

### Node Exporter Service

- **Image:** `bitnami/node-exporter:latest`
- **Ports:** Exposed on port `9100`

## Prometheus Configuration

The `prometheus.yml` file specifies the scraping targets for Prometheus to collect metrics from:

- **Prometheus Job:** Collects metrics from Prometheus itself and Node Exporter.
- **Node Exporter Job:** Collects metrics from Node Exporter.
- **IPFS Job:** Collects metrics from IPFS nodes with a specific metrics path.


## Usage

1. Ensure Docker and Docker Compose are installed on your system.
2. Clone this repository: `git clone https://github.com/yourusername/docker-monitoring.git`.
3. Navigate to the cloned directory: `cd docker-monitoring`.
4. Update the IP addresses in `prometheus.yml` with the appropriate IP addresses for your setup.
5. Start the monitoring stack using Docker Compose: `docker-compose up -d`.
6. Access Prometheus at `http://localhost:9090` and Grafana at `http://localhost:3000`.
7. Log in to Grafana (default credentials: username `admin`, password `admin`) and configure data sources and dashboards as needed.

