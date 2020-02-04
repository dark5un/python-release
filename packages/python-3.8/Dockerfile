FROM ubuntu

ENV DEBIAN_FRONTEND=noninteractive
ENV TZ=Europe/London

RUN apt update && \
    apt install -y wget build-essential less zlib1g-dev openssl libssl-dev \
        libreadline-gplv2-dev libncursesw5-dev libssl-dev libsqlite3-dev tk-dev \
        # libgdbm-dev libc6-dev libbz2-dev libffi-dev libffi6 && \
        libgdbm-dev libc6-dev libbz2-dev && \
    wget https://www.python.org/ftp/python/3.8.1/Python-3.8.1.tgz && \
    wget https://github.com/libffi/libffi/releases/download/v3.3/libffi-3.3.tar.gz && \
    tar xzvf libffi-3.3.tar.gz && \
    cd libffi-3.3 && \
    ./configure --prefix="/var/vcap/packages/python-3.8" && make && make install && cd - && \
    tar xzvf Python-3.8.1.tgz && \
    cd Python-3.8.1 && \
    LDFLAGS="-Wl,-rpath -Wl,/var/vcap/packages/python-3.8/lib" CFLAGS='-fPIC' ./configure --prefix="/var/vcap/packages/python-3.8" && \
    make && make install

# ./configure --prefix=/var/vcap/packages/python-3.8 && 
    
# export PYTHONPATH=$PYTHONPATH:/var/vcap/packages/python-3.8/lib/python3.8/site-packages
# pip3 install kafka-utils
