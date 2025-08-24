
FROM node:22-alpine


WORKDIR /usr/src/app


COPY package.json package-lock.json ./
RUN npm install -g @angular/cli && npm install


COPY . .


EXPOSE 8081

#replace serve with build for evenligter image
CMD ["ng", "serve", "--host", "0.0.0.0", "--port", "8081"]

