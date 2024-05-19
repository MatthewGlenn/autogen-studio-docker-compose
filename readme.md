# AutoGen Studio with Docker Compose
![GitHub Actions Workflow Status](https://img.shields.io/github/actions/workflow/status/matthewglenn/autogen-studio-docker-compose/build.yaml)
![Image Version](https://ghcr-badge.egpl.dev/matthewglenn/autogen-studio-docker-compose/latest_tag?color=%2344cc11&ignore=latest&label=version&trim=)


## Overview

This README provides instructions for installing, configuring, and managing the AutoGen Studio application using Docker Compose. For more information about AutoGen Studio, visit: https://microsoft.github.io/autogen/blog/2023/12/01/AutoGenStudio/

This is a fork of of Dan Murfitt's repo https://github.com/danmurf/autogen-studio-docker-compose

## Prerequisites

Make sure you have the following:

- Docker
- Docker Compose
- An OpenAI API Key.

## Installation

### Using Docker run
1. Run this docker compose run commmand, replacing the OPEN_API_KEY with your own.
```bash
docker run -d \                                                     
  --name autogenstudio \
  -p 8081:8081 \
  -e OPENAI_API_KEY=$OPENAI_API_KEY \
  --restart unless-stopped \
  ghcr.io/matthewglenn/autogen-studio-docker-compose:latest
```

### Using Docker Compose
1. Use this docker compose file, replacing the OPEN_API_KEY with your own or using a value in the an `.env` file.
```yaml
version: "3"
services:
  autogenstudio:
    container_name: autogenstudio
    image: ghcr.io/matthewglenn/autogen-studio-docker-compose:latest
    ports:
      - 8081:8081
    environment:
      - OPENAI_API_KEY=$OPENAI_API_KEY
    restart: unless-stopped
```

1. Build and start the AutoGen Studio application using Docker Compose:

```bash
docker-compose up
```

## Accessing the container
Access Autogen Studio using http://localhost:8081

## Important Note

Please be mindful of your OpenAI (or any other provider) API key usage when using AutoGen Studio. Excessive API usage may result in high charges. By using this application, you acknowledge and accept responsibility for monitoring and controlling your API usage.
