FROM alpine:latest

WORKDIR /app/dist
COPY ./dist /app/dist
COPY Caddyfile /app/Caddyfile

RUN apk add --update caddy

CMD ["caddy", "run", "--config", "/app/Caddyfile", "--adapter", "caddyfile"]