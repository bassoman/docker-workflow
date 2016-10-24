# Set the base image to Ubuntu
FROM    nodejs-dev

# File Maintainer
MAINTAINER Jon Lancelle

# Install Node.js and other dependencies
RUN apt-get update && \
    apt-get -y install build-essential
#    apt-get -y install python build-essential

# Provides cached layer for node_modules
ADD package.json /tmp/package.json
RUN cd /tmp && npm install
RUN mkdir -p /src && cp -a /tmp/node_modules /src/

# Define working directory
WORKDIR /src
ADD . /src

# Expose port
EXPOSE  8080

# Run app using nodemon
CMD ["nodemon", "/src/index.js"]
