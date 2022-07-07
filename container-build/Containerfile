# Use the httpd-parent image as base
FROM quay.io/amr_fahmy/httpd-parent

LABEL io.k8s.display-name="Apache Server" \
      io.k8s.description="A bisic Apache HTTP Server child image" \
      io.openshift.expose-service="8080:http" \
      io.openshift.tags="apache, httpd"
      
EXPOSE 8080

RUN sed -i "s/Listen 80/Listen 8080/g" /etc/httpd/conf/httpd.conf
RUN sed -i "s/#ServerName www.example.com:80/ServerName 0.0.0.0:8080/g" /etc/httpd/conf/httpd.conf
RUN sed -i "s/ServerName 0.0.0.0:80/ServerName 0.0.0.0:8080/g" /etc/httpd/conf/httpd.conf


#RUN chgrp -R 0 /etc/httpd

RUN chgrp -R 0 /var/log/httpd /var/run/httpd && \
    chmod -R g=u /var/log/httpd /var/run/httpd
    
#RUN chgrp -R 0 /var/log/httpd && \
#    chmod -R g=u /var/log/httpd

USER 1001
    


      

