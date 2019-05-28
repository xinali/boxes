FROM 32bit/ubuntu:16.04

MAINTAINER xina1i daitaomail@gmail.com

ENV DEBIAN_FRONTEND noninteractive

# prequirements
RUN apt update && apt upgrade -y && \
    apt install -y python python-pip python3-pip git vim curl wget sudo zsh wget curl g++ gdb make cmake tmux

# install some python packages
RUN pip install ropgadget

# install gef 
RUN git clone https://github.com/hugsy/gef.git /opt/gef

# install peda
RUN git clone https://github.com/longld/peda.git /opt/peda

#install pwndbg
RUN git clone https://github.com/pwndbg/pwndbg.git /opt/pwndbg && \
    cd /opt/pwndbg && \
    ./setup.sh

# install pwntools
RUN apt install -y python2.7 python-pip python-dev git libssl-dev libffi-dev build-essential && pip install pwntools

# install radare2
RUN git clone https://github.com/radare/radare2.git /opt/radare2 && \
        cd /opt/radare2 && bash sys/user.sh

# get dotfiles
RUN git clone https://github.com/xinali/dotfiles ~/.dotfiles && cd ~/.dotfiles && make


# set locale to en_US.UTF-8
RUN apt install -y locales && locale-gen en_US.UTF-8

WORKDIR /root
ENTRYPOINT ["bash"]