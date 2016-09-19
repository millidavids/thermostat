FROM ruby:2.3.1-alpine
MAINTAINER David Yurek <david.a.yurek@gmail.com>

ENV BUILD_PACKAGES="curl-dev ruby-dev build-base bash" \
    DEV_PACKAGES="zlib-dev libxml2-dev libxslt-dev tzdata yaml-dev postgresql-dev" \
    RUBY_PACKAGES="ruby-json yaml nodejs"

    RUN apk update && \
        apk upgrade && \
        apk add --update\
        $BUILD_PACKAGES \
        $DEV_PACKAGES \
        $RUBY_PACKAGES && \
        rm -rf /var/cache/apk/* && \
        mkdir -p /usr/src/app

ONBUILD WORKDIR /usr/src/app
ONBUILD COPY . /usr/src/app
ONBUILD EXPOSE 3000
ONBUILD RUN bundle config build.nokogiri --use-system-libraries && \
            bundle install && \
            bundle clean
