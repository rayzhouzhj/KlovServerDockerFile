#
# Klov + MongoDB Dockerfile
#
# Pull base image.
FROM ubuntu:16.04

# Install java
RUN apt-get update && apt-get install -y sudo
RUN sudo apt-get update && sudo sudo apt-get install -y default-jre

# Install MongoDB.
RUN \
  apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 0C49F3730359A14518585931BC711F9BA15703C6 && \
  echo "deb [ arch=amd64 ] http://repo.mongodb.org/apt/ubuntu trusty/mongodb-org/3.4 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.4.list && \
  apt-get update && \
  sudo apt-get install -y mongodb-org && \
  rm -rf /var/lib/apt/lists/*

# Define mountable directories.
VOLUME ["/data/db"]

# Expose ports.
#   - 27017: process
#   - 28017: http
#   - 8012:  Klov
EXPOSE 27017
EXPOSE 28017
EXPOSE 8012

# Run Mongod and Extent Server
COPY klov-0.0.3 klov-0.0.3

# Define working directory.
WORKDIR /klov-0.0.3


ENTRYPOINT mongod & java -jar klov-0.0.3.jar
