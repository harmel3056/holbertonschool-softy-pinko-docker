## 2. Front-end
For this task, start by making a copy of your task1 directory and name it task2. We have created a very simple API server with one route that returns “Hello, World!” and now we want to create a web page to view content from our API server in the context of a more full front-end. Before creating our front end, let’s reorganize this project a bit in our task2 directory.
- Create a new directory named back-end inside of your task2 directory.
- Move all of the files currently in task2 inside of the new back-end directory.

> You should have api.py and Dockerfile inside of your new task2/back-end directory.
- Create a new task2/front-end directory
- Inside your new task2/front-end, clone this repository -> https://github.com/atlas-school/softy-pinko-front-end

With the softy-pinko-front-end directory and files in place, we need to create a new Dockerfile in your task2/front-end directory.

In order to host and distribute our front-end content we will use a static web server named Nginx; there are many others that can be used, but this one is rather simple to get started with and conveniently has a Docker image that we can use which is pre-installed.
- In the new task2/front-end/Dockerfile, instead of using the latest ubuntu version, use the latest version of nginx.
- Your softy-pinko-front-end files must be copied to /var/www/html/softy-pinko-front-end on the Docker image.
- Create an Nginx config file named softy-pinko-front-end.conf inside of the task2/front-end directory. This file must be copied to the Docker image to /etc/nginx/conf.d/default.conf and must include all of the configuration settings required to get your site to show up when visiting the URL.

> When researching Nginx config files, the only section you’ll need in the softy-pinko-front-end.conf file is the “server” section. Pay attention to the syntax used to set up a port to listen to (recommendation: port 9000), the name of the server, the location, and the index file to use.

### softy-pinko-front-end.conf
```
server {
// Replace with your Nginx server configuration
}
```
At the end of this process, you should have a front end that is accessible like the following:
### Terminal
```
Dereks-MacBook-Pro:task2 derekwebb$ docker build -f ./front-end/Dockerfile -t softy-pinko-front-end:task2 ./front-end
[+] Building 0.6s (8/8) FINISHED                                                                                                          
 => [internal] load build definition from Dockerfile                                                                                 0.0s
 => => transferring dockerfile: 37B                                                                                                  0.0s
 => [internal] load .dockerignore                                                                                                    0.0s
 => => transferring context: 2B                                                                                                      0.0s
 => [internal] load metadata for docker.io/library/nginx:latest                                                                      0.5s
 => [internal] load build context                                                                                                    0.0s
 => => transferring context: 34.13kB                                                                                                 0.0s
 => [1/3] FROM docker.io/library/nginx:latest@sha256:af296b188c7b7df99ba960ca614439c99cb7cf252ed7bbc23e90cfda59092305                0.0s
 => CACHED [2/3] COPY ./softy-pinko-front-end /var/www/html/softy-pinko-front-end                                                    0.0s
 => CACHED [3/3] COPY ./softy-pinko-front-end.conf  /etc/nginx/conf.d/default.conf                                                   0.0s
 => exporting to image                                                                                                               0.0s
 => => exporting layers                                                                                                              0.0s
 => => writing image sha256:5aeebcbf58006d92aa190103a44fa395f2e51a42cc7452a3561ce42af3b2aa46                                         0.0s
 => => naming to docker.io/library/softy-pinko-front-end:task2                                                                       0.0s
Dereks-MacBook-Pro:task2 derekwebb$ docker run -p 9000:9000 -it --rm --name softy-pinko-front-end-task2 softy-pinko-front-end:task2
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: /etc/nginx/conf.d/default.conf differs from the packaged version
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
2023/06/12 17:00:32 [notice] 1#1: using the "epoll" event method
2023/06/12 17:00:32 [notice] 1#1: nginx/1.25.0
2023/06/12 17:00:32 [notice] 1#1: built by gcc 10.2.1 20210110 (Debian 10.2.1-6) 
2023/06/12 17:00:32 [notice] 1#1: OS: Linux 5.15.49-linuxkit
2023/06/12 17:00:32 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1048576:1048576
2023/06/12 17:00:32 [notice] 1#1: start worker processes
2023/06/12 17:00:32 [notice] 1#1: start worker process 28
2023/06/12 17:00:32 [notice] 1#1: start worker process 29
2023/06/12 17:00:32 [notice] 1#1: start worker process 30
2023/06/12 17:00:32 [notice] 1#1: start worker process 31
2023/06/12 17:00:32 [notice] 1#1: start worker process 32
2023/06/12 17:00:32 [notice] 1#1: start worker process 33
2023/06/12 17:00:32 [notice] 1#1: start worker process 34
2023/06/12 17:00:32 [notice] 1#1: start worker process 35
```