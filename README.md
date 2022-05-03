# firebase-cli
Simple install of nodejs, npm and firebase-cli

## Usage

Run container and get shell with firebase tools:

`docker run -it --rm rglonek/firebase-cli`

## Build

`docker build -t firebase-cli .`

## Other

Use docker volumes to mount host volume into this container to use files within firebase-cli.

The default workdir location is `/firebase`
