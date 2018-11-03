Build Image based on docker file and resources:

sudo docker build -t img .

Sending build context to Docker daemon  5.632kB
Step 1/7 : FROM node:8
 ---> 5743fe5ce210
Step 2/7 : WORKDIR /usr/src/app
 ---> Using cache
 ---> 9c5d1bf148f2
Step 3/7 : COPY package*.json ./
 ---> Using cache
 ---> 2032f8dc44fd
Step 4/7 : RUN npm install
 ---> Using cache
 ---> 929c90a2b2d7
Step 5/7 : COPY . .
 ---> e4bd45fc81bf
Step 6/7 : EXPOSE 8080
 ---> Running in 56b1a6e75b60
Removing intermediate container 56b1a6e75b60
 ---> 7cb11c129d8d
Step 7/7 : CMD [ "npm", "start" ]
 ---> Running in d191d881e378
Removing intermediate container d191d881e378
 ---> 753d830a72bc
Successfully built 753d830a72bc
Successfully tagged img:latest

View available images:

sudo docker images

REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
img                 latest              753d830a72bc        58 seconds ago      670MB
dapp                latest              340e4a5d06ef        15 minutes ago      670MB
mydockerapp/app     latest              340e4a5d06ef        15 minutes ago      670MB
<none>              <none>              14cf8d7ad187        24 minutes ago      670MB
node                8                   5743fe5ce210        2 weeks ago         667MB
hello-world         latest              dea8dc17fa0c        7 weeks ago         665kB

Run image:

sudo docker run -p 49163:8080 -d img


Test result:

curl -i localhost:49163

HTTP/1.1 200 OK
X-Powered-By: Express
Content-Type: text/html; charset=utf-8
Content-Length: 12
ETag: W/"c-M6tWOb/Y57lesdjQuHeB1P/qTV0"
Date: Sat, 03 Nov 2018 05:44:52 GMT
Connection: keep-alive

Hello world


Clear all docker local data (containers that are not running):

sudo docker system prune -a (docker image prune -a [for unused images only])

WARNING! This will remove:
        - all stopped containers
        - all networks not used by at least one container
        - all images without at least one container associated to them
        - all build cache
Are you sure you want to continue? [y/N] y

Check running containers:

sudo docker container ps (--all)

Stop them:

sudo docker stop [container-id]
