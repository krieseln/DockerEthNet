FROM ubuntu:xenial
ENV TZ='Europe/Berlin'

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

CMD exec geth --bootnodes "enode://$bootnodeId@$bootnodeIp:30301" --networkid "1337" --verbosity=4 --rpc --rpcaddr "0.0.0.0" --rpcport 8545 --rpcapi "eth,web3,net,admin,debug,db,miner,personal" --rpccorsdomain "*" --ws --wsaddr "0.0.0.0" --wsapi "eth,web3,net,admin,debug,db,miner,personal" --wsport 8546 --wsorigins "*" --syncmode="full"

EXPOSE 8545
EXPOSE 8546
EXPOSE 30303