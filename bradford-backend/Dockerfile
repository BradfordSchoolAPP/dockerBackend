FROM ruby:2.5.3

RUN apt-get update -qq && apt-get install -y build-essential libpq-dev nodejs

RUN mkdir /app
WORKDIR /app

ADD backend/Gemfile backend/Gemfile.lock /app/

RUN gem install bundler
RUN bundle install

COPY backend /app/

CMD ["sh", "-c", "bundle exec rake db:drop db:create db:migrate && bundle exec rails s -b 0.0.0.0 -p 3000"]
