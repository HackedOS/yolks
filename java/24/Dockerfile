# Use the official Ubuntu base image
FROM --platform=$TARGETOS/$TARGETARCH ghcr.io/graalvm/jdk-community:24

# Install necessary tools
RUN         apt update -y \
    && apt install -y curl ca-certificates openssl git wget tar sqlite3 fontconfig tzdata iproute2 libfreetype6 \
    && useradd -d /home/container -m container

RUN java -version

USER container
ENV USER=container HOME=/home/container
WORKDIR /home/container

COPY ./../entrypoint.sh /entrypoint.sh
CMD [ "/bin/bash", "/entrypoint.sh" ]
