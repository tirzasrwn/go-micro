# go-micro

## About

## Opening Project
Using Visual Studio Code, File -> Open Workspace from File ... -> workspace.code-workspace

## Port List
```
App-Name                    Docker-Container-Port   Local-Port
Front-End                   -                       8000
Broker-Service              80                      8080
Authentication-Service      80                      8081
Postgres                    5432                    5431
Mailhog                     1025                    1025
Mailhog-Web-Interface       8025                    8025
Mail-Service                80                      -
RabbitMQ                    5672                    5672
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
Cleaning image to save some space
```sh
docker system prune
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

# Go Tool for gRPC
Install
```sh
go install google.golang.org/protobuf/cmd/protoc-gen-go@v1.27
go install google.golang.org/grpc/cmd/protoc-gen-go-grpc@v1.2
```
Step to using gRPC:
* Define your .proto file
* Generate gRPC code from command line
```sh
# Go to directory that having .proto file.
sudo apt install -y protobuf-compiler # Install protoc
# Make sure you can run protoc-gen-go and protoc-gen-go-grpc, you can just export the path.
protoc --go_out=. --go_opt=paths=source_relative --go-grpc_out=. --go-grpc_opt=paths=source_relative logs.proto
# It will auto generate two files that you don't want to edit.
```
Reference:
* https://grpc.io/docs/protoc-installation/