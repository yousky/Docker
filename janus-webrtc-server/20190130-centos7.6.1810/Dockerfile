FROM centos:7.6.1810

# install base dependencies
RUN yum install -y epel-release \
    && yum update -y \
    && yum install -y libmicrohttpd-devel jansson-devel openssl-devel libsrtp-devel sofia-sip-devel glib2-devel opus-devel libogg-devel libcurl-devel pkgconfig gengetopt libconfig-devel libtool autoconf automake

# install extra build tools
RUN yum install -y sudo make git doxygen graphviz cmake which gtk-doc

# build & install libsrtp
RUN cd ~ \
    && git clone https://github.com/cisco/libsrtp.git \
    && cd libsrtp \
    && git checkout v2.2.0 \
    && ./configure --prefix=/usr --libdir=/usr/lib64 --enable-openssl \
    && make shared_library \
    && sudo make install

## build & install libnice
# RUN cd ~ \
#     && git clone https://gitlab.freedesktop.org/libnice/libnice.git \
#     && cd libnice \
#     && ./autogen.sh \
#     && ./configure --prefix=/usr && make && sudo make install
RUN yum install -y libnice-devel

# build & install usrsctp for Data Channels
RUN cd ~ \
    && git clone https://github.com/sctplab/usrsctp \
    && cd usrsctp \
    && ./bootstrap \
    && ./configure --prefix=/usr --libdir=/usr/lib64 \
    && make && sudo make install

## build & install libwebsockets
# RUN cd ~ \
#    && git clone https://libwebsockets.org/repo/libwebsockets \
#    && cd libwebsockets \
#    && git checkout v2.4-stable \
#    && mkdir build \
#    && cd build \
#    && cmake -DLWS_MAX_SMP=1 -DCMAKE_INSTALL_PREFIX:PATH=/usr -DCMAKE_C_FLAGS="-fpic" .. \
#    && make \
#    && sudo make install

# build & install janus gateway
RUN cd ~ \
    && git clone https://github.com/meetecho/janus-gateway.git \
    && cd janus-gateway \
    && sh autogen.sh \
    && ./configure --prefix=/opt/janus --disable-websockets --disable-rabbitmq --disable-mqtt --enable-docs \
    && make CFLAGS='-std=c99' \
    && make install \
    && make configs

# cleanup


VOLUME ["/opt/janus"]
WORKDIR /opt/janus

