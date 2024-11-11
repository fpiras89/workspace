# Workspace

This repository folder contains the necessary files to run a Docker Compose based workspace which includes:
- Prometheus as a monitoring tool
- Grafana as a visualization tool
- Tempo as a distributed tracing tool
- Loki as a log aggregation tool
- Otel Collector as a telemetry data collector
- Microsoft SQL Server as a RDBMS
- Keycloak as a IAM

Run `docker compose -f ./docker-compose.yaml up --build`

This command will do the following:
- Start MSSQL container
- Create the Keycloak database using **mssql-tools**
- Build a custom Keycloak image based on the offical one
- Start Keycloak in develpment mode
- Start Prometheus, Grafana, Tempo, Loki and Otel Collector containers