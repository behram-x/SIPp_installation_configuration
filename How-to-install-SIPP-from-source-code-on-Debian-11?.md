## Install Pre-requisites

```
sudo apt install cmake build-essential libncurses-dev libssl-dev libpcap-dev libnet1 lksctp-tools libsctp-dev
```
## Download sipp source code and extract it.

```
cd /usr/local/src/
wget -c https://github.com/SIPp/sipp/releases/download/v3.6.1/sipp-3.6.1.tar.gz
tar -xvf sipp-3.6.1.tar.gz
cd sipp-3.6.1/ 

```
## Compile and make with TLS, PCAP Play and SCTP support.

```
cmake . -DUSE_SSL=1 -DUSE_PCAP=1 -DUSE_SCTP=1
make
```
