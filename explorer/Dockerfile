FROM node:14.4-alpine
ENV TZ='Europe/Berlin'

WORKDIR "/opt"

RUN apk add --update git make g++ && \
    git clone https://github.com/litithio/blockchain-explorer.git

WORKDIR "/opt/blockchain-explorer"
RUN npm install

CMD npm run start

EXPOSE 8080