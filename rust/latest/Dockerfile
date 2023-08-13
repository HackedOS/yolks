FROM        --platform=$TARGETOS/$TARGETARCH rust:slim

RUN         apt update \
                && apt -y install git dnsutils curl iproute2 ffmpeg \
                && mkdir /home/container

WORKDIR     /home/container

COPY        ./../entrypoint.sh /entrypoint.sh
CMD         ["/bin/bash", "/entrypoint.sh"]