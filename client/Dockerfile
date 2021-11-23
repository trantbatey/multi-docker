FROM node:16-alpine as builder

ENV PORT=2080
RUN rm /bin/sh && ln -s /bin/bash /bin/sh

RUN mkdir -p /app
WORKDIR '/app'

COPY package.json ./
RUN npm install
COPY ./ ./
RUN npm run build
EXPOSE 3000

FROM nginx:alpine
COPY --from=builder /app/build /usr/share/nginx/html
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
CMD sed -i -e 's/$PORT/'"$PORT"'/g' /etc/nginx/conf.d/default.conf && nginx -g 'daemon off;'
