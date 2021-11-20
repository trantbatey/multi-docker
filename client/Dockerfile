FROM node:16-alpine as builder

RUN mkdir -p /app
WORKDIR '/app'

COPY package.json ./
RUN npm install
COPY ./ ./
RUN npm run build
EXPOSE 3000

FROM nginx
RUN if [ "$PORT" = "" ]; then export PORT=2080; fi 
RUN export DOCKER_CLIENT_TIMEOUT=120; export COMPOSE_HTTP_TIMEOUT=120
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf.template
COPY docker-entrypoint.sh /
ENTRYPOINT ["/docker-entrypoint.sh"]
RUN ["chmod", "+x", "/docker-entrypoint.sh"]
CMD ["nginx", "-g", "daemon off;"]
COPY --from=builder /app/build /usr/share/nginx/html
