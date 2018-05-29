# Running testnet node with Docker

1. Install Docker and Docker Compose  
Instructions for ubuntu 16-04 [here](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-16-04) and [here](https://docs.docker.com/compose/install/#prerequisites), don't skip optional step 2, docker without sudo

2. To get the latest docker-compose.yml file, clone the repository
```
git clone https://github.com/GravityProtocol/gravity-testnet-docker
cd gravity-testnet-docker
```

3. Pull the latest docker image
```
docker-compose pull
```

4. Launch the node
```
docker-compose up
```
