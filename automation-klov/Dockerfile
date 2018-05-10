#
# Klov + MongoDB Dockerfile
#
# Pull base image.
FROM ubuntu:16.04

# Install MongoDB.
RUN apt-get update && apt-get install -y sudo
RUN sudo apt-get update && sudo sudo apt-get install -y default-jre
RUN rm -rf /var/lib/apt/lists/*

# Define mountable directories.
VOLUME ["/data/db"]

# Expose ports.
#   - 8012:  Klov
EXPOSE 8012

# Run Mongod and Extent Server
COPY klov-0.1.0 klov-0.1.0

# Define working directory.
WORKDIR /klov-0.1.0

ENTRYPOINT java -jar klov-0.1.0.jar
