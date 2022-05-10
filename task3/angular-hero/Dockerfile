# Stag1 - Build
FROM node:13-alpine as BUILD
WORKDIR /app
COPY package.json .
RUN npm install
COPY . .
RUN npm run build
# Stag2 - 1
FROM nginx:1.21.6-alpine
COPY --from=BUILD /app/dist /usr/share/nginx/html
COPY nginx.conf /etc/nginx/nginx.conf