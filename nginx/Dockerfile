FROM nginx:alpine
ENV PORT=2080
RUN rm /bin/sh && ln -s /bin/bash /bin/sh
COPY ./default.conf /etc/nginx/conf.d/default.conf
CMD sed -i -e 's/$PORT/'"$PORT"'/g' /etc/nginx/conf.d/default.conf && nginx -g 'daemon off;'
