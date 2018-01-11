# create a file named Dockerfile
FROM node:7-alpine

RUN apk add --no-cache git nano curl && mkdir /portal && mkdir /portal/config

WORKDIR /portal

RUN git clone https://github.com/wedevelopmx/contactolegislativo.git \ 
  && npm install pm2 bower -g \
  && cd contactolegislativo \ 
  && npm install \
  && bower update -a

COPY ./config.json /portal/config
COPY ./process.json /portal

RUN cp config/config.json contactolegislativo/app/config 

EXPOSE 80

CMD ["pm2-docker", "process.json"]
