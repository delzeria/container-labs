## docker build
# base image
FROM node:latest

# define env variables
ENV APP_PORT=5000 APP_DIR=/fortune

# create APP_DIR & cd into it
WORKDIR ${APP_DIR}

# copy files to APP_DIR
ADD main.js .
ADD package.json .
# directories must have a target name
ADD public public
ADD views views

# install libraries from package.json
RUN npm install

## docker run
EXPOSE ${APP_PORT}

# health check configurtion
HEALTHCHECK --interval=60s --timeout=5s --retries=3 \
CMD curl -f -s http://localhost:${APP_PORT}/health || exit 1

# how the image should be executed
ENTRYPOINT [ "node", "main.js" ]
