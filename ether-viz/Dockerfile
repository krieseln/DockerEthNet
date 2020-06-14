FROM node:14.4-alpine
ENV TZ='Europe/Berlin'

WORKDIR "/opt"

RUN apk add --update git make g++ && \
    git clone https://github.com/krieseln/ether-viz.git

WORKDIR "/opt/ether-viz/EtherVizApp/client"
RUN npm install

CMD npm run start &&\
    sh

EXPOSE 3000