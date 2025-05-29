# Use NodeJs image
FROM node:slim

# Install requirements for the emulators
RUN apt-get update && \
    apt-get install -y vim chromium ca-certificates-java && \
    apt-get install nano && \
    apt-get clean && \
    update-ca-certificates -f

# Change working directory
WORKDIR /functions/src

# Set Java Environment to be reference by the emulators
ENV JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64/
RUN export JAVA_HOME

# Install Firebase tools to allow CLI to work
RUN npm install -g firebase-tools

# Copy installation files first
COPY ./functions/package.json /functions
COPY ./functions/tsconfig.json /functions

# Install package.json packages
RUN npm install

# Copy files in src folder
COPY ./functions/src /functions/src

# Copy the rest of the files
COPY ./functions/.env /functions/.env
COPY ./firebase.json /
COPY ./firestore.indexes.json /
COPY ./firestore.rules /
COPY ./storage.rules /

# Change working directory
WORKDIR /functions

# Build and watch project files
ENTRYPOINT [ "npm", "run", "build:watch"]
