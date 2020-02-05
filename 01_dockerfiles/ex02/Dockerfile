FROM ruby

RUN apt-get update && apt-get upgrade -y
RUN gem install rails
RUN apt-get install nodejs -y
RUN apt-get install yarn -y
WORKDIR /opt/
RUN rm -rf /opt/app
RUN git clone https://github.com/codefresh-contrib/ruby-on-rails-sample-app.git app
WORKDIR app/
RUN bundle install
RUN rails db:migrate
#docker run  -p 10.11.2.15:3000:3000 <image name>
