FROM node:16-alpine as builder

RUN mkdir -p /app
WORKDIR '/app'

COPY package.json ./
RUN npm install
COPY ./ ./
RUN npm run build
RUN if [ "${PORT}" = "" ]; then export PORT=3000; fi
EXPOSE $PORT

FROM nginx
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html
