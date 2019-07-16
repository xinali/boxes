FROM ubuntu:latest

MAINTAINER xina1i daitaomail@gmail.com

ENV DEBIAN_FRONTEND noninteractive

# prequirements
RUN apt update && \
    apt install -y git vim curl wget zsh wget curl gdb make cmake tmux gcc clang

#install pwndbg
RUN git clone https://github.com/pwndbg/pwndbg.git /opt/pwndbg && \
    cd /opt/pwndbg && \
    ./setup.sh

# get dotfiles
RUN git clone https://github.com/xinali/dotfiles ~/.dotfiles && cd ~/.dotfiles && make

# install afl
RUN  git clone https://github.com/mirrorer/afl && cd afl && make && make install

# set locale to en_US.UTF-8
RUN apt install -y locales && locale-gen en_US.UTF-8

WORKDIR /root
ENTRYPOINT ["zsh"]