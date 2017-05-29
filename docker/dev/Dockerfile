FROM ubuntu:16.04
MAINTAINER Jay Ng "jayng@seekasia.com"

COPY ./requirements.txt /tmp/

ENV LC_ALL=C.UTF-8
ENV LANG=C.UTF-8

RUN apt-get -y update \
    && apt-get -y install apt-utils python3-pip redis-server \
    && apt-get clean \
    && mkdir -p /app-home \
    && mkdir -p /app-log \
    &&pip3 install -r /tmp/requirements.txt \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN mkdir -p /jayng \
    && mkdir -p /jayng/samele-base

CMD ["gunicorn", "--chdir", "/jayng/samele-base/simpleweb/",  "-c", "/jayng/samele-base/simpleweb/gunicorn.conf", "wsgi:app"]
#ENTRYPOINT ["/bin/bash"]
