# use node image
FROM node:14

## BUILD
# Env variable
# for application
ENV APP_DIR=/app APP_PORT=3000

#for database
ENV DB_USER=root DB_PASSWORD=changeit

# change dir to $APP_DIR
WORKDIR ${APP_DIR}

ADD main.js .
ADD package.json .
ADD package-lock.json .

ADD config config
ADD public public
ADD views views

#install dependencies
RUN npm install

## RUNTIME
HEALTHCHECK --interval=30s --timeout=5s --start-period=10s --retries=3 \ 
    CMD curl -f -s http://localhost:${APP_PORT}/health || exit 1


# expose
EXPOSE ${APP_PORT}

# run program
ENTRYPOINT [ "node", "main.js" ]