FROM ruby:2 AS build

RUN gem install bundler

COPY . .

RUN bundle install

# COPY . /workspace
ENV JEKYLL_ENV=production
RUN bundle exec jekyll build

FROM nginx:1

WORKDIR /app
COPY _app /app
COPY --from=build _site /app/site

CMD ["/app/start.sh"]