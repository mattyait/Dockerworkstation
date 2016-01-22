FROM centos:centos6
RUN yum install epel-release -y
RUN yum install git -y
RUN yum install golang -y
RUN yum install wget -y
RUN yum install tar -y

#ENV APP_PATH /mnt/go/src
#RUN mkdir -p $APP_PATH
#ENV GOPATH /mnt/go/


ENV HUGO_VERSION=0.15
ENV APP_PATH /mnt/hugo
RUN mkdir -p $APP_PATH
ENV HUGOPATH /opt/hugo/
RUN mkdir -p $HUGOPATH


ADD https://github.com/spf13/hugo/releases/download/v${HUGO_VERSION}/hugo_${HUGO_VERSION}_linux_amd64.tar.gz $HUGOPATH
RUN cd $HUGOPATH && tar -xvf hugo_${HUGO_VERSION}_linux_amd64.tar.gz
RUN cd $HUGOPATH && rm -f hugo_${HUGO_VERSION}_linux_amd64.tar.gz
RUN mkdir ~/bin
RUN ln -s $HUGOPATH/hugo_${HUGO_VERSION}_linux_amd64/hugo_${HUGO_VERSION}_linux_amd64 ~/bin/hugo

ADD hugosite/. $APP_PATH
VOLUME $APP_PATH
WORKDIR $APP_PATH

EXPOSE 1313
CMD ["/root/bin/hugo", "--buildDrafts","--theme='hugoscroll'","--watch server"]