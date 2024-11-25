FROM openresty/openresty:1.21.4.1-0-bullseye-fat

ENV LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH

RUN sed -i "s@http://\(deb\|security\).debian.org@https://mirrors.tencent.com@g" /etc/apt/sources.list && \
    apt-get update && \
    apt-get install -y binutils make csh g++ sed gawk autoconf automake autotools-dev libtool cmake wget unzip && \
    cd /opt/ && \
    wget "https://github.com/mongodb/libbson/archive/refs/heads/master.zip" -O  libbson.zip && unzip libbson.zip && \
    wget "https://github.com/isage/lua-cbson/archive/refs/heads/master.zip" -O lua-cbson.zip && unzip lua-cbson.zip && \
    wget "https://github.com/isage/lua-resty-moongoo/archive/refs/heads/master.zip" -O lua-resty-moongoo.zip && unzip lua-resty-moongoo.zip && \
    cd /opt/libbson-master && ./autogen.sh && make && make install && \
    cd /opt/lua-cbson-master && mkdir build && cd build && cmake .. && make && make install && \
    cd /opt/lua-resty-moongoo-master && cp -avR lib/resty/ /usr/local/openresty/lualib/ && \
    rm -rf /var/lib/apt/lists/* && rm -rf /opt/*

