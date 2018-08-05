FROM ubuntu:latest

WORKDIR /tmp

ENV commit_id HEAD

RUN apt-get update && apt-get install -y \
	git \
	libtool \
	libusb-1.0.0-dev \
	librtlsdr-dev \
	rtl-sdr \
	build-essential \
	autoconf \
	cmake \
	pkg-config

RUN git clone https://github.com/merbanan/rtl_433.git && \
    cd rtl_433 && \
    git reset --hard $commit_id && \
    mkdir build && \
    cd build && \
    cmake ../ && \
    make && \
    make install

WORKDIR /

ENTRYPOINT ["/rtl_433.sh"]

COPY rtl_433.sh /rtl_433.sh
RUN chmod +x /rtl_433.sh
