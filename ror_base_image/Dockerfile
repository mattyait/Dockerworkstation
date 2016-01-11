#Installing all required packages
FROM centos:centos6
RUN yum install epel-release -y
RUN yum install cyrus-sasl-devel -y
RUN yum install mysql-devel -y
RUN yum install postgresql-libs -y
RUN yum install postgresql-devel -y
RUN yum install ImageMagick-devel -y
RUN yum install which -y
RUN yum install tar -y
RUN yum install wget -y
RUN yum install vim -y
RUN yum install nodejs -y

#Installing ruby 2.1.2 with RVM and passenger with nginx module
RUN curl -sSL https://rvm.io/mpapis.asc | gpg2 --import - && \
curl -L get.rvm.io | bash -s stable && \
source /etc/profile.d/rvm.sh && \
/bin/bash -l -c "rvm install 2.1.2" && \
/bin/bash -l -c "gem install rack -v=1.6.4" && \
/bin/bash -l -c "gem install passenger --no-ri --no-rdoc --no-http-proxy --source http://rubygems.org" && \
yum install libcurl-devel -y && \
/bin/bash -l -c "passenger-install-nginx-module --auto --auto-download --prefix=/usr/local/nginx --extra-configure-flags='--with-http_gzip_static_module --with-http_ssl_module'"

#Install s3cmd tool
RUN yum install python-dateutil -y
RUN wget http://sourceforge.net/projects/s3tools/files/s3cmd/1.5.0-rc1/s3cmd-1.5.0-rc1.tar.gz
RUN tar -xzvf s3cmd-1.5.0-rc1.tar.gz
RUN cd s3cmd-1.5.0-rc1 && python setup.py install
RUN s3cmd --version
