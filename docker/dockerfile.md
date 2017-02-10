
```
FROM centos
MAINTAINER cts

ENV TZ "Asia/Shanghi"
ENV TERM xterm

RUN yum install -y git python-devel && \
    yum install -y --enablerepo=epel pwgen python-pip && \
    yum clean all

RUN pip install supervisor
ADD supervisord.conf /etc/supervisord.conf

EXPOSE 22
```
