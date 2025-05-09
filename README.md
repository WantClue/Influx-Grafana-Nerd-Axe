# Influx-Grafana-Nerd-Axe

A Docker-based monitoring solution for Nerd*Axe miner using InfluxDB and Grafana.

## Overview

This project provides a ready-to-use monitoring stack for Nerd*Axe miner operations, specifically designed for Nerd*Axe miners. It includes:

- InfluxDB 2.7 for time-series data storage
- Grafana for visualization and dashboarding
- Pre-configured dashboards for mining metrics
- Docker Compose for easy deployment

## Features

- Real-time monitoring of mining statistics
- Track hashrate, blocks found, and mining difficulty
- Pre-configured Grafana dashboard
- Persistent storage for both InfluxDB and Grafana
- Environment-based configuration

## Requirements

- Docker and Docker Compose
- Git (for cloning the repository)

## Quick Start

1. Clone this repository:
   ```
   git clone https://github.com/wantclue/Influx-Grafana-Nerd-Axe.git
   cd Influx-Grafana-Nerd-Axe
   ```

2. Configure environment variables
   ```
   # Edit the .env file with your preferred settings
   nano .env
   ```

3. Start the services:
   ```
   docker-compose up -d
   ```

4. Access Grafana:
   - Open your browser and navigate to `http://localhost:3000`
   - Login with the credentials specified in your `.env` file
   - The pre-configured dashboard should be available

## Configuration

### Environment Variables

The following environment variables can be configured in the `.env` file:

- `DOCKER_INFLUXDB_INIT_MODE`: InfluxDB initialization mode (default: setup)
- `DOCKER_INFLUXDB_INIT_USERNAME`: InfluxDB admin username
- `DOCKER_INFLUXDB_INIT_PASSWORD`: InfluxDB admin password
- `DOCKER_INFLUXDB_INIT_ORG`: InfluxDB organization name
- `DOCKER_INFLUXDB_INIT_BUCKET`: InfluxDB bucket name
- `DOCKER_INFLUXDB_INIT_RETENTION`: Data retention period (0 = infinite)
- `DOCKER_INFLUXDB_INIT_ADMIN_TOKEN`: InfluxDB admin token
- `DOCKER_GRAFANA_INIT_USERNAME`: Grafana admin username
- `DOCKER_GRAFANA_INIT_PASSWORD`: Grafana admin password

## Dashboard

The pre-configured dashboard includes:
- Total blocks found
- Total best difficulty
- Current session statistics
- Real-time hashrate gauge
- Historical hashrate graph
- Mining statistics over time

## Data Structure

The dashboard expects data in the following format:
- Measurement: `{network}_stats` (e.g., `mainnet_stats`)
- Fields:
  - `hashing_speed`: Current hashrate in GH/s
  - `total_blocks_found`: Total number of blocks found
  - `total_best_difficulty`: Total best difficulty
  - `best_difficulty`: Current best difficulty
  - `accepted`: Number of accepted shares
  - `not_accepted`: Number of rejected shares
  - `pool_errors`: Number of pool errors

## Persistence

Data is persisted using Docker volumes:
- `influxdb-data`: Stores InfluxDB data
- `grafana-data`: Stores Grafana data

## License

This project is licensed under the MIT License - see the LICENSE file for details.