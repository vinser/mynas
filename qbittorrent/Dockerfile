FROM debian:buster-slim

# set version label
ARG BUILD_DATE
ARG VERSION
ARG QBITTORRENT_VERSION
LABEL build_version="Linuxserver.io version:- ${VERSION} Build-date:- ${BUILD_DATE}"
LABEL maintainer="sparklyballs, thelamer"

# environment settings
ARG DEBIAN_FRONTEND="noninteractive"
ENV HOME="/config" \
XDG_CONFIG_HOME="/config" \
XDG_DATA_HOME="/config"

# install qbitorrent

# add qbt service 
COPY ./qbittorrent.service /etc/systemd/system/qbittorrent.service

RUN \
    apt install qbittorrent-nox && \
    systemctl daemon-reload && \
    systemctl start qbittorrent && \   
    systemctl enable qbittorrent

# ports and volumes
EXPOSE 6881 6881/udp 8080
VOLUME /config /downloads

