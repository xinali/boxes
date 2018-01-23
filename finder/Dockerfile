FROM ubuntu:latest

MAINTAINER xina1i daitaomail@gmail.com

# prequirements
RUN apt update && apt upgrade -y && apt install -y python python-pip python3-pip git vim curl wget sudo zsh gcc g++ make

RUN pip install -U pip && pip  install -y requests ipython 

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
