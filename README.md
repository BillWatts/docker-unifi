# Docker Unifi
Simple docker container for run a stand-alone [Unifi Controller](unifi controller download).


### Getting The Docker Image

To obtain the docker image Unifi Controller choose one of the following options:

- Build docker image:

  ```
  git clone git@github.com:BillWatts/docker-unifi.git
  cd docker-unifi
  docker build -t unifi .
  ```

- Pull image from Dockerhub:

  ```
  docker pull billwatts/unifi
  ```

### Running The Docker Image

To get your Docker image up and running choose one of the following options:

- Via `docker`:
   ```
   docker run -d -v /path-to-data:/usr/lib/unifi/data -p 8080:8080 -p 8081:8081 -p 8443:8443 -p 8880:8880 -p 3478:3478  unifi
   ```

- Via `docker-compose`:
  ```
  docker-compose up -d
  ```

### Configuration

#### Environment Variables
| Variable Name           | Values                 | Behaviour                                                                            | Default value   |
| ----------------------: | :--------------------: | :----------------------------------------------------------------------------------- | :-------------: |
|     DOCKER_UNIFI_DATA   |  String     | Path to the configuration on the the local machine (`docker-compose` only)                      | Unset           |
|   DOCKER_UNIFI_VERSION  |  String     | Specifies the version of Unifi you wish to deploy.                                              | Latest Version  |

To use environment variables with `Docker` you can do so by using the following:

- Via `docker run`:
  ```
  docker run -e DOCKER_UNIFI_VERSION=5.0.7 ... billwatts/unifi
  ```

  or

  ```
  echo "DOCKER_UNIFI_VERSION=5.0.0" >> path/to/docker-unifi/.env
  docker run --envfile=./.env ... billwatts/unifi
  ```

- Via `docker-compose`:
  ```
  echo "DOCKER_UNIFI_DATA=./data" >> path/to/docker-unifi/.env
  docker-compose up
  ```
