FROM stackbrew/debian:sid
MAINTAINER Johan Euphrosine <proppy@google.com>

RUN echo 'deb-src http://http.debian.net/debian sid main' >> /etc/apt/sources.list
RUN apt-get update && apt-get install -yq git dh-golang golang build-essential devscripts equivs libcrypt-ssleay-perl lintian --no-install-recommends
ADD . /usr/src/golang-gocapability/debian/
WORKDIR /usr/src/golang-gocapability
RUN mk-build-deps -irt'apt-get --no-install-recommends -yq' debian/control

RUN (cd /tmp && bash -x /usr/src/golang-gocapability/debian/README.Source && cp *.orig.tar.gz /usr/src)
RUN (cd /usr/src && tar xvzf /usr/src/*.orig.tar.gz)

CMD [ "debuild", "-us", "-uc" ]