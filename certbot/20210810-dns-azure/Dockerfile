FROM certbot/certbot:v1.18.0

RUN pip install certbot-dns-azure

VOLUME ["/etc/letsencrypt"]
WORKDIR /etc/letsencrypt/www

ENTRYPOINT ["certbot"]
