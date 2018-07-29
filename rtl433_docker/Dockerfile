FROM ubuntu:latest

WORKDIR /tmp

ENV commit_id HEAD

RUN apt-get update && apt-get install -y \
 rtl-sdr \
 librtlsdr-dev \
 librtlsdr0 \
 git \
 automake \
 libtool \
 cmake 

RUN git clone https://github.com/merbanan/rtl_433.git && \
    cd rtl_433 && \
    git reset --hard $commit_id && \
    mkdir build && \
    cd build && \
    cmake ../ && \
    make && \
    make install && \
    cd / && \
    rm -rf /tmp/rtl_433


WORKDIR /

ENTRYPOINT ["/rtl_433.sh"]

COPY rtl_433.sh /rtl_433.sh
RUN chmod +x /rtl_433.sh
