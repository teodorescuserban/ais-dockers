FROM teodorescuserban/atman-base:latest

MAINTAINER Serban Teodorescu, teodorescu.serban@gmail.com

ENV DEBIAN_FRONTEND noninteractive
RUN locale-gen en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8

RUN mkdir -p /etc/service/squid
ADD run /etc/service/squid/
RUN chmod u+x /etc/service/squid/run

ADD squid.conf /etc/squid3/
ADD list_zone_ok /etc/squid3/
ADD list_domenii_ok /etc/squid3/

EXPOSE 3128

RUN /etc/my_init.d/00_regen_ssh_host_keys.sh
CMD ["/sbin/my_init"]

