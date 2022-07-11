# go-micro

## About

## Opening Project
Using Visual Studio Code, File -> Open Workspace from File ... -> workspace.code-workspace

## Port List
```
Front-End:          8000
Broker-Service:     8080
```

## Docker
Running docker compose
```sh
cd ./project
sudo docker compose up -d
sudo docker compose up -d --build --force-recreate --no-deps # forced to rebuild image
```