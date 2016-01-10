FROM ubuntu:wily
MAINTAINER caktux

ENV DEBIAN_FRONTEND noninteractive

# Usual update / upgrade
RUN apt-get update
RUN apt-get upgrade -q -y
RUN apt-get dist-upgrade -q -y

# Install Ethereum
RUN apt-get install -q -y software-properties-common
RUN add-apt-repository ppa:ethereum/ethereum
RUN add-apt-repository ppa:ethereum/ethereum-dev
RUN apt-get update
RUN apt-get install -q -y geth

# Configure test-net cluster
RUN mkdir -p /go/src/github.com/j4ustin/go-ethereum
RUN mkdir /etc/testnet/
COPY . /go/src/github.com/j4ustin/go-ethereum
WORKDIR /go/src/github.com/j4ustin/go-ethereum
RUN cp ./CustomGenesis.json /etc/testnet/CustomGenesis.json

EXPOSE 8545
EXPOSE 30303

ENTRYPOINT ["/usr/bin/geth"]
