# letsencrypt certbot Dockerfile

Default Work Volume : /etc/letsencrypt

## Prerequisite

Create directory `/etc/letsencrypt/www`.

Exposing the `/etc/letsencrypt/www` directory through a web server.

Nginx setting example
```yml
server {
        listen       80;
        
        access_log  /var/log/nginx/default.access.log;
        location /.well-known/acme-challenge {
                root /etc/letsencrypt/www;
        }
        index index;
}
```

## Usage

Mount the host `/etc/letsencrypt` directory to `/etc/letsencrypt`.

The following example equal "certbot certonly --webroot -w /etc/letsencrypt/www -d sample.com -d www.sample.com -d api.sample.com".
```yml

docker run -it --rm -v /etc/letsencrypt:/etc/letsencrypt yousky/certbot:20170221-centos7.3.1611 certonly --webroot -w /etc/letsencrypt/www -d sample.com -d www.sample.com -d api.sample.com

```


See also [certbot](https://certbot.eff.org/docs/using.html#webroot).

## License
Released under the [MIT license](http://opensource.org/licenses/MIT).
