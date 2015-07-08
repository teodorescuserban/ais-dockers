FROM teodorescuserban/atman-base:latest

MAINTAINER Serban Teodorescu, teodorescu.serban@gmail.com

ENV DEBIAN_FRONTEND=noninteractive \
    LANG=en_US.UTF-8 \
    LANGUAGE=en_US:en \
    LC_ALL=en_US.UTF-8

RUN locale-gen en_US.UTF-8 && \
    apt-get -qq -y update && \
    apt-get install -qq -y \
    squid3 && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* && \
    mkdir -p /etc/service/squid

COPY run /etc/service/squid/
RUN chmod u+x /etc/service/squid/run

COPY ["sq*.conf","list_*_ok", /etc/squid3/

VOLUME ['/var/spool/squid3', '/var/log/squid3']

EXPOSE 3128

RUN /etc/my_init.d/00_regen_ssh_host_keys.sh

CMD ["/sbin/my_init"]
