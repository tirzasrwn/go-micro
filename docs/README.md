# go-micro

## About

## Opening Project
Using Visual Studio Code, File -> Open Workspace from File ... -> workspace.code-workspace

## Port List
```
Front-End:              8000
Broker-Service:         8080
Authentication-Service: 8000
```

## Docker
Running docker compose
```sh
cd ./project
sudo docker compose up -d
sudo docker compose up -d --build --force-recreate --no-deps # forced to rebuild image
# To run without sudo, try to add current user into docker group.
# Reference: https://askubuntu.com/questions/477551/how-can-i-use-docker-without-sudo
sudo usermod -aG docker $USER # Restart
```

## Makefile
To speed up the work.
```sh
cd ./project
make down # To make docker image broker-service down.
make up_build # To build broker-service and run docker compose.
make start # To build and run front-end in local.
make down # To stop front-end in local.
```