FROM registry.access.redhat.com/ubi8/ubi:8.0

MAINTAINER Red Hat Training <training@redhat.com>

LABEL io.k8s.description=" A basic Apache server" \
			io.k8s.display-name="Apache Htop" \
			io.openshift.expose-service="8080:http" \
			io.openshift.tags="Apache, httpd"

ENV DOCROOT=/var/www/html 

RUN yum install -y --nodocs --disableplugin=subscription-manager httpd && \ 
		yum clean all --disableplugin=subscription-manager -y && \
		echo "Hello from the httpd-parent container!" > ${DOCROOT}/index.html && \
		sed -i "s/Listen 80/Listen 8080/g" /etc/httpd/conf/httpd.conf && \
    sed -i "s/#ServerName www.example.com:80/ServerName 0.0.0.0:8080/g" /etc/httpd/conf/httpd.conf && \
		chgrp -R 0 /var/log/httpd /var/run/httpd && \
    chmod -R g=u /var/log/httpd /var/run/httpd 

COPY src ${DOCROOT}/
ADD do288-apps.tar ./

ONBUILD COPY src/ ${DOCROOT}/

EXPOSE 8080

USER 1001

# Launch httpd

CMD /usr/sbin/httpd -DFOREGROUND
