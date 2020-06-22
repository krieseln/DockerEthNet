FROM ubuntu:focal
ENV TZ='Europe/Berlin'

RUN apt-get update \
     && apt-get install -y wget software-properties-common


WORKDIR "/root"

RUN add-apt-repository -y ppa:ethereum/ethereum

RUN apt-get update \
     && apt-get install -y ethereum

ENV nodekeyhex=""
CMD exec bootnode -nodekeyhex $nodekeyhex

EXPOSE 30301/udp
EXPOSE 30303/udp
