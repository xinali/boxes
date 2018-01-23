FROM ubuntu:latest

MAINTAINER xina1i daitaomail@gmail.com

# prequirements
RUN apt update && apt upgrade -y && apt install -y python python-pip python3-pip git vim curl wget sudo zsh

#  gef
# 1. install keystone-engine
RUN apt install -y g++ gdb  gcc cmake python-capstone
RUN git clone https://github.com/keystone-engine/keystone ~/keystone && cd ~/keystone && mkdir build  \
		&& cd build && ../make-share.sh && make install && ldconfig

# install some python packages
RUN pip install -U pip && pip install ipython requests 

# install gef requirements
RUN pip3 install -U pip && pip3 install keystone-engine capstone unicorn ropper retdec-python 

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
	cd /opt/radare2 && \
		git fetch --tags && \
		git checkout $(git describe --tags $(git rev-list --tags --max-count=1)) && \
		./sys/install.sh  && \
		make symstall

# zsh
RUN wget https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O /tmp/install.sh && bash /tmp/install.sh
COPY ./configfiles/zshrc /root/.zshrc

# vim
COPY ./configfiles/vimrc /root/.vimrc

# gdb config
COPY ./configfiles/gdbinit /root/.gdbinit

# set locale to en_US.UTF-8
RUN apt install -y locales && locale-gen en_US.UTF-8


WORKDIR /root
ENTRYPOINT ["/usr/bin/zsh"]
