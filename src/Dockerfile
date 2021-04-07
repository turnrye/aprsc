FROM debian:buster
RUN apt-get update
RUN apt-get install -y gcc make libevent-dev
RUN groupadd -g 999 appuser && \
    useradd -r -u 999 -g appuser appuser
WORKDIR /app
RUN chown appuser:appuser /app
COPY . .
RUN ./configure && make && make install
USER appuser
RUN mkdir data && mkdir logs
EXPOSE 10152/tcp
EXPOSE 10152/udp
EXPOSE 14580/tcp
EXPOSE 14580/udp
EXPOSE 8080/udp
VOLUME /config
CMD ["/app/aprsc", "-c", "/config/aprsc.conf"]