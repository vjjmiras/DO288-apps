FROM registry.access.redhat.com/ubi7

RUN yum update && \
    yum install -y httpd && \
    yum clean all -y 

LABEL io.openshift.tags=web \
      io.k8s.description="This is a demo image to build a web server" \
      io.openshift.expose-services=80/http:web_http

WORKDIR /var/www/html

ENV MYSQL_USER=user \
    MYSQL_PASSWORD=passwd

VOLUME /var/www/data

USER root

RUN echo "This is the content of the web server" >./index.html

# ENTRYPOINT

CMD ["/usr/sbin/httpd","-D","FOREGROUND"]
