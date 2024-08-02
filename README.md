# Pharmarcy-Prescription-Management-System

UYP SYSTEM BUILD PROCEDURE

Building with compose
```sh
docker compose up -d --build
```

Detail build with docker
Building docker image
```sh
docker image build -t uyp-system-app .	
```

Create Network
```sh
docker network create db-network
```
Postgres Database
```sh
docker run -d --name postgres-db --network db-network  -e POSTGRES_DB=uypDb -e POSTGRES_USER=puser -e POSTGRES_PASSWORD=pass -v postgresdata:/var/lib/postgresql/data  -d -p 5432:5432 postgres:15
```
Launch application
```sh
docker run -d --name uyp-app --network db-network -e POSTGRES_HOST=postgres-db  -e POSTGRES_DB=uypDb -p 8080:8080 uyp-system-app
```
Navigate to: http://localhost:8080/
