FROM python:3.8.6-buster

LABEL MAINTAINER="Thanh Hoang <hhthanh.hust@gmail.com>"

ENV GROUP_ID=1000 \
    USER_ID=1000

WORKDIR /var/www/

ADD ./requirements.txt /var/www/requirements.txt
RUN pip install -r requirements.txt
ADD . /var/www/
RUN pip install gunicorn

RUN addgroup --gid $GROUP_ID www
RUN adduser --disabled-login -u $USER_ID --ingroup www www --shell /bin/sh

USER www
RUN pwd
RUN ls
EXPOSE 5000

#CMD ["tail", "-f", "/dev/null"]
CMD [ "gunicorn", "-w", "4", "--bind", "0.0.0.0:5000", "wsgi:app"]