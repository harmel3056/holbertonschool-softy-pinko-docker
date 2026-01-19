FROM ubuntu:latest
# uses latest version of ubuntu as base image
RUN apt-get update && \
    apt-get install -y python3 python3-pip
RUN rm /usr/lib/python*/EXTERNALLY-MANAGED && \
    pip3 install flask
# runs updates and installs softwares
CMD ["python3", "api.py"]
# runs flask app upon build completion
WORKDIR /app
# sets working directory
COPY api.py /app
# takes local file and places it inside the image’s filesystem at /app
