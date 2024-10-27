# Workspace

This repository contains the necessary files to run a Docker Compose based workspace which includes:
- Microsoft SQL Server as a RDBMS
- Keycloak as a IAM

Run `docker compose -f ./docker-compose.yaml up --build`

This command will do the following:
- Start MSSQL container
- Create the Keycloak database using **mssql-tools**
- Build a custom Keycloak image based on the offical one
- Start Keycloak in develpment mode