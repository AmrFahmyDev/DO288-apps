# Use the httpd-parent image as base
FROM quay.io/redhattraining/httpd-parent

RUN yum install --nodocs --disableplugin=subscreption-manager htop -y && \
		yum clean all -y

