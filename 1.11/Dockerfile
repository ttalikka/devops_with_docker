FROM ubuntu:latest

COPY backend-example-docker backend-example
WORKDIR /backend-example
EXPOSE 8000

RUN apt-get update && apt-get install -y curl
RUN curl -sL https://deb.nodesource.com/setup_10.x | bash
RUN apt-get update && apt-get install -y nodejs
RUN node -v && npm -v
ENV FRONT_URL=http://localhost:5000
RUN npm install
CMD npm start
