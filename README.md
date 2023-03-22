# Docker_UAV_MarsLab

## Installation Instraction on Ubuntu Focal 20.04 (LTS)
Instractions below are from
https://docs.docker.com/engine/install/ubuntu/
and
https://docs.docker.com/desktop/install/ubuntu/
### Set up the repository

1. Update the apt package index and install packages to allow apt to use a repository over HTTPS:
```bush
 sudo apt-get update

 sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```
2. Add Docker’s official GPG key:
```bush
sudo mkdir -m 0755 -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```
3. Use the following command to set up the repository:
```bush
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

### Install Docker Engine
1. Update the apt package index:
```bush
sudo apt-get update
```
2. Install Docker Engine, containerd, and Docker Compose.
```bush
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```
3. Verify that the Docker Engine installation is successful by running the hello-world image:
```bush
sudo docker run hello-world
```

### Install Docker Desktop
#### Prerequisites
For non-Gnome Desktop environments, gnome-terminal must be installed: 
```bush
sudo apt install gnome-terminal
```
#### Installation
1. Download latest version
https://desktop.docker.com/linux/main/amd64/docker-desktop-4.17.0-amd64.deb?utm_source=docker&utm_medium=webreferral&utm_campaign=docs-driven-download-linux-amd64

2. Enter the donlowded floder and find the .deb file. Install the package with apt as follows:
```bush
sudo apt-get update
sudo apt-get install ./docker-desktop-<version>-<arch>.deb
```
3. Launch Docker Desktop
```bush
systemctl --user start docker-desktop
```


## Essential Docker Commands
### 1. Docker Search
To search for public images on the Docker hub. It will return information about the image name, description, stars, official and automated.
```bush
docker search MySQL
```
### 2. Docker Pull
To pull from docker hub with specific version
```bush
docker pull --platform linux/arm64/v8 mysql:5.6
```
### 3.Docker Images
To list all the images with details
```bush
docker images
```
### 4. Docker Run
To create a container for images. --env option to set a mandatory environment variable and --detach option to run the container in the background.
```bush
docker run -d mysql
```
### 5.Docker Lists
To list all the running containers
```bush
docker ps

docker ps -a
```
### 6.Docker Stop and Restart
To stop a container
```bush
docker stop id******
```

To restart a container
```bush
docker restart id*****
```

### 7. Docker Rename
For exp change the container name from compassionate_fermi to test_db
```bush
docker rename compassionate_fermi test_db
```

### 8. Docker Exec
To run a new command in a running container.

Access the running container test_db by running the following command. It’s helpful if we want to access the MySQL command line and execute MySQL queries.
```bush
docker exec -it test_db bash
mysql -uroot -pmy-secret-pw
SHOW DATABASES;
```

### 9. Docker Logs
```bush
docker logs test_db
```

### 10. Docker Remove
```bush
docker rm test_db
```
















