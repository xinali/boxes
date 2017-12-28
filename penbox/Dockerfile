FROM ubuntu:latest

MAINTAINER xina1i daitaomail@gmail.com

# prequirements
RUN apt update && apt upgrade -y && apt install -y python python-pip python3-pip git vim curl wget sudo zsh

RUN pip install -U pip && pip  install -y requests ipython 

# sqlmap


# zsh
COPY ./configfiles/zshrc /root/.zshrc

# vim
COPY ./configfiles/vimrc /root/.vimrc


WORKDIR /root
ENTRYPOINT ["/usr/bin/zsh"]
