
FROM        --platform=$TARGETOS/$TARGETARCH openjdk:21-bullseye

RUN         apt update -y \
    && apt install -y curl ca-certificates openssl git tar sqlite3 fontconfig tzdata iproute2 libfreetype6 \
    && useradd -d /home/container -m container

USER        container
ENV         USER=container HOME=/home/container
WORKDIR     /home/container

COPY        ./../entrypoint.sh /entrypoint.sh
CMD         [ "/bin/bash", "/entrypoint.sh" ] 
