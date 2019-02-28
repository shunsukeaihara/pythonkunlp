FROM python:3.6-alpine

MAINTAINER aihara

ARG JUMANPP_VERSION=1.01
ARG JUMAN_VERSION=7.01
ARG KNP_VERSION=4.19

# JUMAN + KNP
RUN apk add --update --no-cache --virtual=build-deps boost-dev g++ make zlib-dev \
    && wget -q http://lotus.kuee.kyoto-u.ac.jp/nl-resource/jumanpp/jumanpp-${JUMANPP_VERSION}.tar.xz \
    && tar Jxfv jumanpp-${JUMANPP_VERSION}.tar.xz \
    && cd jumanpp-${JUMANPP_VERSION} \
    && ./configure \
    && make \
    && make install \
    && cd ../ \
    && rm -rf jumanpp-${JUMANPP_VERSION} \
    && rm jumanpp-${JUMANPP_VERSION}.tar.xz \
    && wget -q http://nlp.ist.i.kyoto-u.ac.jp/nl-resource/juman/juman-${JUMAN_VERSION}.tar.bz2 \ 
    && tar xf juman-${JUMAN_VERSION}.tar.bz2 \
    && cd juman-${JUMAN_VERSION} \ 
    && ./configure \
    && make \
    && make install \
    && cd ../ \
    && rm -rf juman-${JUMAN_VERSION} \
    && rm juman-${JUMAN_VERSION}.tar.bz2 \
    && wget -q http://nlp.ist.i.kyoto-u.ac.jp/nl-resource/knp/knp-${KNP_VERSION}.tar.bz2 \
    && tar xfv knp-${KNP_VERSION}.tar.bz2 \
    && cd knp-${KNP_VERSION} \
    && ./configure --enable-utf8-only --with-charset=utf8 \
    && make \
    && make install \
    && cd ../ \
    && rm -rf knp-${KNP_VERSION} \
    && rm -rf knp-${KNP_VERSION}.tar.bz2 \
    && rm -rf /var/cache/* \
    && apk del build-deps \
    && apk add --update --no-cache boost zlib \
    && rm -rf /var/cache/apk \
    && mkdir /var/cache/apk
    && rm -rf /root/.cache

CMD /bin/sh