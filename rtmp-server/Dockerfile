FROM ubuntu:16.04

# Install ffmpeg from ubuntu packages
RUN apt-get update && apt-get upgrade -y && apt-get clean \
	apt-get install -y ffmpeg

# Install nginx with rtmp module enabled from source using latest release
ENV NGINX_VERSION 1.11.3

RUN apt-get install -y build-essential git wget openssl libpcre3-dev zlib1g-dev libssl-dev && \
	mkdir /src && mkdir /conf && mkdir /logs && mkdir /html && \
	cd /src && \
	wget http://nginx.org/download/nginx-${NGINX_VERSION}.tar.gz && \
	tar xvzf nginx*.tar.gz && \
	rm *.tar.gz && \
	git clone --depth=1 https://github.com/arut/nginx-rtmp-module && \
	cd nginx-${NGINX_VERSION} && \
	./configure --add-module=/src/nginx-rtmp-module --conf-path=/conf/nginx.conf --error-log-path=/logs/error.log --http-log-path=/logs/access.log --with-http_ssl_module && \
	make && make install && \
	apt-get remove -y build-essential git wget && apt-get autoremove -y

# Copy default nginx configuration
COPY nginx.conf /conf/nginx.conf

# Expose ports
EXPOSE 80 443 1935

CMD ["/usr/local/nginx/sbin/nginx"]
