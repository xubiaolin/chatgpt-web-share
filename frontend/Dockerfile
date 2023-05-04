FROM node:latest as builder
ARG NODE_ENV
ENV RUN_ENV=${NODE_ENV}

ADD . /app
WORKDIR /app

RUN npm config set registry https://registry.npmmirror.com \
    && npm install -g pnpm\
    && pnpm install\
    && pnpm run build

FROM nginx:latest

COPY --from=builder /app/dist /usr/share/nginx/html
COPY --from=builder /app/nginx.conf /etc/nginx/conf.d/app.conf

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
