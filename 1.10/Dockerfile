FROM ubuntu:latest

COPY frontend-example-docker frontend-example
WORKDIR /frontend-example
EXPOSE 5000

RUN apt-get update && apt-get install -y curl
RUN curl -sL https://deb.nodesource.com/setup_10.x | bash
RUN apt-get update && apt-get install -y nodejs
RUN node -v && npm -v
ENV API_URL=http://localhost/api/
RUN npm install
CMD npm start
