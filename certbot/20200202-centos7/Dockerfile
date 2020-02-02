FROM centos:7

RUN yum install -y epel-release \ 
	&& yum update -y \
	&& yum install -y certbot

VOLUME ["/etc/letsencrypt"]
WORKDIR /etc/letsencrypt/www

ENTRYPOINT ["certbot"]
