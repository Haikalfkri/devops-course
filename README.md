# Devops Course


## Docker Commands

`docker ps -> list of all running containers`
`docker ps -a -> list all of containers`
`docker stop container_id -> stop running container`
`docker stop container1 container2 container3 -> stop multiple container`
`docker rm container_id -> to remove container`
`docker container prune -> remove all of the containers`
`docker rmi nginx -> remove an image`
`docker rmi nginx hello-world image3 image4 -> remove multiple image`

`docker build -t mern-backend .`
`docker run -p 5000:5000 --name backend mern-backend`
`docker run -p 5000:5000 --name backend --env-file .env mern-backend`

`docker-compose up --build`
`docker-compose up --build -d`
`docker-compose down`
`docker-compose logs, docker-compose logs container_name`