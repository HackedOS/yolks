# Use the official Ubuntu base image
FROM ubuntu:latest

# Install necessary tools
RUN         apt update -y \
    && apt install -y curl ca-certificates openssl git wget tar sqlite3 fontconfig tzdata iproute2 libfreetype6 \
    && useradd -d /home/container -m container

# Download GraalVM
RUN wget https://github.com/graalvm/graalvm-ce-dev-builds/releases/download/24.2.0-dev-20241001_2238/graalvm-community-java24-linux-amd64-dev.tar.gz

# Extract GraalVM
RUN tar -xzf graalvm-community-java24-linux-amd64-dev.tar.gz -C /opt

# Set environment variables
ENV JAVA_HOME=/opt/graalvm-community-openjdk-24+17.1
ENV PATH=$JAVA_HOME/bin:$PATH

# Clean up
RUN rm graalvm-community-java24-linux-amd64-dev.tar.gz

# Verify installation
RUN java -version

USER container
ENV USER=container HOME=/home/container
WORKDIR /home/container

COPY ./../entrypoint.sh /entrypoint.sh
CMD [ "/bin/bash", "/entrypoint.sh" ]
