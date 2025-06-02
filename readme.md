```yml
version: '3.8'  # Specify the Compose file format version

services:       # Define services (containers)
  service_name:  # Name of the service
    image: image_name:tag  # Specify the image to use
    build:        # Build options (if applicable)
      context: ./path/to/context  # Build context
      dockerfile: Dockerfile  # Specify Dockerfile (if different)
    ports:        # Map ports
      - "host_port:container_port"
    volumes:      # Mount volumes
      - host_path:container_path
    environment:  # Environment variables
      VAR_NAME: value
    depends_on:   # Define service dependencies
      - other_service
    networks:     # Specify networks
      - network_name
    command: command_to_run  # Override the default command
    restart: always  # Restart policy
    deploy:           # Parameters for deployment
      replicas: 3    # Number of replicas
      resources:      # Resource constraints
        limits:
          cpus: '0.5' # Limit the number of CPUs
          memory: 512M # Limit memory usage
        reservations:
          cpus: '0.25' # Reserved CPUs
          memory: 256M  # Reserved memory
      restart_policy: # Restart policy
        condition: on-failure
        max_attempts: 5
        window: 30s
      placement:      # Placement constraints
        constraints:
          - node.role == manager
      update_config:  # Update configuration
        parallelism: 1
        delay: 10s
        max_failure_ratio: 0.3
        order: start-first
      rollback_config: # Rollback configuration
        parallelism: 1
        delay: 10s
        max_failure_ratio: 0.3
        order: start-first

networks:       # Define networks (optional)
  network_name:
    driver: bridge  # Specify network driver (e.g., bridge, overlay)

volumes:        # Define volumes (optional)
  volume_name:

```

## 📕 Docker Guide and Refrence file

> [Docker Compose Refrence guide](https://docs.docker.com/reference/compose-file/)

> [Docker file Refrence](https://docs.docker.com/reference/dockerfile/)

> [Docker Docs](https://docs.docker.com/reference/)