# Dockerfile for the Wagtail demo

# FIXME: Test prepare_db.sh ..

# Web admin: admin / test

FROM ubuntu
MAINTAINER Tom Dyson

RUN apt-get install -y build-essential
RUN apt-get install -y git
RUN apt-get install -y postgresql  libpq-dev
RUN apt-get install -y python-dev  python-pip
RUN apt-get install -y libxml2-dev libxslt1-dev
RUN apt-get install -y libjpeg-dev

RUN cd / && git clone https://github.com/torchbox/wagtaildemo.git
RUN cd /wagtaildemo && pip install -r requirements/dev.txt

ADD prepare_db.sh /wagtaildemo/
RUN bash /wagtaildemo/prepare_db.sh

CMD /etc/init.d/postgresql start
CMD cd /wagtaildemo
CMD ./manage.py runserver 0.0.0.0:8000
CMD echo "Wagtail started on port 8000"
