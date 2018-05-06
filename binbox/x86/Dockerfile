FROM 32bit/ubuntu:16.04

MAINTAINER xina1i daitaomail@gmail.com

ENV DEBIAN_FRONTEND noninteractive
# prequirements
RUN apt update && apt upgrade -y && apt install -y python python-pip python3-pip git vim curl wget sudo zsh wget curl

#  gef
# 1. install keystone-engine
RUN apt install -y g++ gdb  gcc cmake python-capstone
RUN git clone https://github.com/keystone-engine/keystone ~/keystone && cd ~/keystone && mkdir build  \
                && cd build && ../make-share.sh && make install && ldconfig

# install some python packages
# RUN pip install -U pip==9.0.3 && pip install ipython requests keystone-engine capstone unicorn ropper retdec-python 
RUN pip3 install ipython requests keystone-engine capstone unicorn ropper retdec-python 

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

# install libheap                                                                                                          
RUN apt install -y libc6-dbg                                                                                               
RUN git clone https://github.com/cloudburst/libheap && \                                                                   
    pip3 install --user ./libheap/   

# zsh
RUN wget https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O /tmp/install.sh && bash /tmp/install.sh
RUN wget https://gist.githubusercontent.com/xinali/60e6a283f9ce6e9cb6f575928e26be67/raw/7ebc737fb7a5567b80399b5c474791ef6235515d/zshrc \
        -O /root/.zshrc

# vim
RUN wget https://gist.githubusercontent.com/xinali/e5ba9e33d2ab942d35dda7a0bfa98029/raw/d871f503e2aee014def04947d8c81c6d426769e7/vimrc \
        -O /root/.vimrc

# install vim-plug
RUN curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim

# gdb config
RUN wget https://gist.githubusercontent.com/xinali/dd52d3c289984f8f6662afecd50ce484/raw/71de5fe558257e094fc9b23b57badf68426d3e47/gdbinit \
        -O /root/.gdbinit

# set locale to en_US.UTF-8
RUN apt install -y locales && locale-gen en_US.UTF-8


WORKDIR /root
ENTRYPOINT ["zsh"]