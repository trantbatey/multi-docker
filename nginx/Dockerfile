FROM nginx
RUN if [ "$PORT" = "" ]; then export PORT=2080; fi 
RUN export DOCKER_CLIENT_TIMEOUT=120; export COMPOSE_HTTP_TIMEOUT=120
COPY ./default.conf /etc/nginx/conf.d/default.conf.template
COPY docker-entrypoint.sh /
ENTRYPOINT ["/docker-entrypoint.sh"]
RUN ["chmod", "+x", "/docker-entrypoint.sh"]
CMD ["nginx", "-g", "daemon off;"]