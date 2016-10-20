FROM fedora:24
MAINTAINER darmath, darmath.mxo@hotmail.com

#Install and setup Apache httpd
RUN dnf -y --setopt=deltarpm=false install httpd && dnf clean all
ADD run-apache.sh /run-apache.sh
RUN chmod -v +x /run-apache.sh

#Upgrade pip
RUN pip3 install --upgrade pip

#Add and enable mod_wsgi 4.5.7
ADD 01-wsgi.conf /etc/httpd/conf.modules.d/01-wsgi.conf
ADD mod_wsgi.so /usr/lib64/httpd/modules/mod_wsgi.so
RUN chmod -v +x /usr/lib64/httpd/modules/mod_wsgi.so

#Add python application
ADD test.wsgi /var/www/cgi-bin/test.wsgi
RUN chmod -v +x /var/www/cgi-bin/test.wsgi

EXPOSE 80
CMD ["/run-apache.sh"]
