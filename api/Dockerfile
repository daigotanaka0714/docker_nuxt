FROM ruby:3

RUN apt-get update -qq && \
  apt-get install -y \
  build-essential \
  libpq-dev \
  nodejs \
  postgresql-client

WORKDIR /api

COPY Gemfile Gemfile.lock /api/

RUN bundle install