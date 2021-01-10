FROM alpine:latest

EXPOSE 1313

WORKDIR /app

RUN apk add --no-cache hugo

CMD [ "hugo", "server", "--bind", "0.0.0.0", "-s", "/app" ]