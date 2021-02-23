FROM registry.access.redhat.com/ubi7

RUN yum update && \
    yum install -y httpd && \
    yum clean all -y 

LABEL io.openshift.tags=web \
      io.k8s.description="This is a demo image to build a web server" \
      io.openshift.expose-services=8080/http:web_http

WORKDIR /var/www/html

ENV MYSQL_USER=user \
    MYSQL_PASSWORD=passwd

VOLUME /var/www/data

USER root

RUN chgrp -R 0 /run/httpd /var/log/httpd && \
    chmod -R g=u /run/httpd /var/log/httpd && \
    sed -i -e 's,^Listen 80,Listen 8080,' /etc/httpd/conf/httpd.conf && \
    echo "This is the content of the web server" >./index.html

EXPOSE 8080 

# ENTRYPOINT

CMD ["/usr/sbin/httpd","-D","FOREGROUND"]
