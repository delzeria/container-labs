FROM node:latest

ENV DB_HOST=nwdb DB_PORT=3306 DB_USER=root DB_PASSWORD=changeit \ 
    APP_PORT=3000 APP_DIR=/northwind

WORKDIR ${APP_DIR}

ADD main.js .
ADD package.json .

ADD config config
ADD public public
ADD views views

RUN npm install

EXPOSE ${APP_PORT}

HEALTHCHECK --interval=60s --timeout=30s --retries=3 \
CMD curl -f -s http://localhost:${APP_PORT}/health || exit 1

ENTRYPOINT [ "node", "main.js" ]