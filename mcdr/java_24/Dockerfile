FROM mcdreforged/mcdreforged-extra:latest-slim

RUN <<EOT
set -eux
apt-get update -y
apt-get install -y wget curl ca-certificates openssl git tar sqlite3 fontconfig tzdata iproute2
apt-get install -y gettext-base
useradd -d /home/container -m container
EOT

RUN wget https://download.oracle.com/graalvm/24/latest/graalvm-jdk-24_linux-x64_bin.tar.gz

RUN mkdir /opt/graalvm && tar -xzf graalvm-jdk-24_linux-x64_bin.tar.gz -C /opt/graalvm --strip-components=1

ENV JAVA_HOME=/opt/graalvm
ENV PATH=$JAVA_HOME/bin:$PATH

RUN rm graalvm-jdk-24_linux-x64_bin.tar.gz

RUN java -version

USER container
ENV USER=container HOME=/home/container

WORKDIR /home/container
COPY ./../entrypoint.sh ./../start_hook.py ./../start_hook.yml /
CMD ["/bin/bash", "/entrypoint.sh"]

