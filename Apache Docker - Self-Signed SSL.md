**Dockerfile example**

```
FROM php:7.4-apache

MAINTAINER Valerio Galano

# Prepare apt
RUN apt-get update

# Prepare fake SSL certificate
RUN apt-get install -y ssl-cert

# Setup Apache2 mod_ssl
RUN a2enmod ssl

# Setup Apache2 HTTPS env
RUN a2ensite default-ssl.conf

# Work directory
```
