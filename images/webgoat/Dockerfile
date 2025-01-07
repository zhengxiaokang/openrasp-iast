FROM webgoat/webgoat-8.0

LABEL MAINTAINER "OpenRASP <ext_yunfenxi@baidu.com>"

ARG RASP_VERSION

COPY sources.list /etc/apt/sources.list

USER root

#RUN rm -rf /var/lib/apt/lists/* && apt-get -o Acquire::AllowInsecureRepositories=true update && apt-get clean

#RUN apt-get install -y --allow-unauthenticated wget procps curl

RUN sed -i 's|http://deb.debian.org/debian|http://archive.debian.org/debian|g' /etc/apt/sources.list && \
    sed -i 's|http://security.debian.org/debian-security|http://archive.debian.org/debian-security|g' /etc/apt/sources.list && \
        echo 'Acquire::Check-Valid-Until "false";' > /etc/apt/apt.conf.d/99no-check-valid-until && \
        rm -rf /var/lib/apt/lists/* && apt-get -o Acquire::AllowInsecureRepositories=true update && apt-get clean && \
                apt-get install -y wget curl procps

WORKDIR /root/
RUN wget https://packages.baidu.com/app/openrasp/release/${RASP_VERSION}/rasp-java.zip && \
    unzip rasp-java.zip && \
    rm -rf rasp-java.zip && \
    mv rasp-2* rasp-java

COPY config/openrasp.yml /root/rasp-java/rasp/conf/openrasp.yml

COPY start.sh /root/

ENTRYPOINT ["/bin/bash", "/root/start.sh"]
