# guide
## https://docs.docker.com/language/nodejs/build-images/
FROM node:12-alpine
WORKDIR /app
COPY ["package.json", "package-lock.json*", "./"]
RUN npm install
COPY . .
CMD [ "npm", "start" ]