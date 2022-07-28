# Use the httpd-parent image as base
FROM quay.io/redhattraining/httpd-parent

COPY epel-release-latest-8.noarch.rpm ./

RUN yum install -y epel-release-latest-8.noarch.rpm && \
		yum update -y && \
		yum install --nodocs --disableplugin=subscreption-manager htop -y && \
		yum clean all -y

