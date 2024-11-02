# Use the official Ubuntu base image
FROM ubuntu:latest

# Install necessary tools
RUN         apt update -y \
    && apt install -y curl ca-certificates openssl git wget tar sqlite3 fontconfig tzdata iproute2 libfreetype6 \
    && useradd -d /home/container -m container

# Download GraalVM
RUN wget https://github.com/graalvm/oracle-graalvm-ea-builds/releases/download/jdk-24.0.0-ea.19/graalvm-jdk-24.0.0-ea.19_linux-x64_bin.tar.gz

# Extract GraalVM
RUN tar -xzf graalvm-jdk-24.0.0-ea.19_linux-x64_bin.tar.gz -C /opt

# Set environment variables
ENV JAVA_HOME=/opt/graalvm-jdk-24+20.1
ENV PATH=$JAVA_HOME/bin:$PATH

# Clean up
RUN rm graalvm-jdk-24.0.0-ea.19_linux-x64_bin.tar.gz

# Verify installation
RUN java -version

USER container
ENV USER=container HOME=/home/container
WORKDIR /home/container

COPY ./../entrypoint.sh /entrypoint.sh
CMD [ "/bin/bash", "/entrypoint.sh" ]
