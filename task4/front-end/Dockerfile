FROM nginx:latest
# uses latest version of nginx as base image
# Nginx is a software used as a web server, reverse proxy, load balancer, mail proxy, and HTTP cache
COPY softy-pinko-front-end /var/www/html/softy-pinko-front-end
# copies entire directory contents (frontend files) to Nginx's default web-served directory
COPY softy-pinko-front-end.conf /etc/nginx/conf.d/default.conf
# copies config file for Nginx server to Nginx config directory