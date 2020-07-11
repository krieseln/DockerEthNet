FROM ubuntu:focal

RUN echo $TZ > /etc/timezone \
     && apt-get update \
     && apt-get install -y wget software-properties-common

WORKDIR "/root"
RUN add-apt-repository -y ppa:ethereum/ethereum

RUN apt-get update \
     && apt-get install -y ethereum

ARG password
ARG privatekey
RUN echo $password > ~/.accountpassword
RUN echo $privatekey > ~/.privatekey
ADD ./genesis.json ./genesis.json
RUN geth init genesis.json
RUN geth account import --password ~/.accountpassword  ~/.privatekey

ENV address=""
ENV bootnodeId=""
ENV bootnodeIp=""

CMD exec geth --bootnodes "enode://$bootnodeId@$bootnodeIp:30301" --networkid "1337" --verbosity=4 --http --http.addr "0.0.0.0" --http.port 8545 --http.api "eth,web3,net,admin,debug,db,miner,personal" --http.corsdomain "*" --ws --ws.addr "0.0.0.0" --ws.api "eth,web3,net,admin,debug,db,miner,personal" --ws.port 8546 --ws.origins "*" --syncmode="full" --unlock 0x3590aca93338b0721966a8d0c96ebf2c4c87c544 --allow-insecure-unlock

EXPOSE 8545
EXPOSE 8546
EXPOSE 30303