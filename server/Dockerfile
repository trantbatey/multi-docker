FROM node:14.14.0-alpine
ENV PORT=2080
RUN rm /bin/sh && ln -s /bin/bash /bin/sh
WORKDIR "/app"
COPY ./package.json ./
RUN npm install
COPY . .
CMD ["npm", "run", "start"]
