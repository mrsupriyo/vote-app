FROM node:latest

RUN apt-get update
RUN apt-get install -y --no-install-recommends curl tini
RUN rm -rf /var/lib/apt/lists/*

WORKDIR /result

RUN npm install -g nodemon

COPY package*.json ./

RUN npm ci
RUN npm cache clean --force
RUN mv /usr/local/app/node_modules /node_modules

COPY . / result

ENV PORT 80
EXPOSE 80

ENTRYPOINT ["/usr/bin/tini", "--"]
CMD ["node", "server.js"]
