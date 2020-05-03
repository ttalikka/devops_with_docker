FROM ruby:2.6.0

COPY rails-example-project rails-example
WORKDIR /rails-example
EXPOSE 3000

RUN gem install bundler:1.17.2 && bundle install
RUN apt-get update -qq && apt-get install -y nodejs
RUN rails db:migrate
CMD rails s
