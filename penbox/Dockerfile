FROM ubuntu:latest

MAINTAINER xina1i daitaomail@gmail.com

# prequirements
RUN apt update && apt install -y python python3 git vim curl wget sudo zsh gcc g++ make

# install pip2 && pip3
RUN wget https://bootstrap.pypa.io/get-pip.py -O /tmp/get-pip.py \
    && python /tmp/get-pip.py
    && python3 /tmp/get-pip.py

# sqlmap

# install nmap
RUN git clone https://github.com/nmap/nmap ~/nmap && cd ~/nmap \ 
		&& ./configure \
		&& make \
		&& make install

# compile masscan
RUN set -x \
        && mkdir -p /opt/penwok \
        && git clone https://github.com/robertdavidgraham/masscan /opt/penwok && cd masscan \
        && make -j
# zsh
COPY ./configfiles/zshrc /root/.zshrc

# vim
COPY ./configfiles/vimrc /root/.vimrc

WORKDIR /root
ENTRYPOINT ["/usr/bin/zsh"]