FROM httpd:2.4.39

RUN apt-get update && apt-get install -y git libapache2-mod-security2 
RUN cd /tmp && git clone https://github.com/SpiderLabs/owasp-modsecurity-crs.git \
  && mv /tmp/owasp-modsecurity-crs/crs-setup.conf.example /etc/modsecurity/crs-setup.conf \
  && mv /tmp/owasp-modsecurity-crs/rules/ /etc/modsecurity/

RUN echo "Include conf/extra/httpd-exo.conf" >> /usr/local/apache2/conf/httpd.conf
RUN cp /etc/modsecurity/modsecurity.conf-recommended /etc/modsecurity/modsecurity.conf && mkdir -p /var/log/apache2/ && chown www-data:www-data /var/log/apache2

COPY httpd-exo.conf /usr/local/apache2/conf/extra/

