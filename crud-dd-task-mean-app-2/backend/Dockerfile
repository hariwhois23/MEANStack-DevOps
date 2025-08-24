FROM node:22-alpine

WORKDIR usr/src/app

RUN addgroup -S appgroup && adduser -S appuser -G appgroup
USER appuser

COPY package.json .
RUN npm install

COPY . .

EXPOSE 8080

CMD [ "node", "server.js"] 

