# Use the httpd-parent image as base
FROM quay.io/redhattraining/httpd-parent

LABEL io.k8s.description=" A basic Apache server" \
			io.k8s.display-name="Apache Htop" \
			io.openshift.expose-service="8080:http" \
			io.openshift.tags="Apache, httpd"

RUN sed -i "s/Listen 80/Listen 8080/g" /etc/httpd/conf/httpd.conf && \
		sed -i "s/#ServerName www.example.com:80/ServerName 0.0.0.0:8080/g" /etc/httpd/conf/httpd.conf 

COPY epel-release-latest-8.noarch.rpm ./

RUN yum install -y epel-release-latest-8.noarch.rpm && \
		yum update -y && \
		yum install --nodocs --disableplugin=subscreption-manager htop -y && \
		yum clean all -y

RUN chgrp -R 0 /var/log/httpd /var/run/httpd && \
		chmod -R g=u /var/log/httpd /var/run/httpd

EXPOSE 8080

USER 1001


