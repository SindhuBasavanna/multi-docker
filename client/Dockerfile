FROM node:alpine as builder
workdir /app
COPY ./package.json ./
RUN npm install
COPY . .
RUN npm run build

FROM nginx
expose 3000
COPY ./nginx/default.conf /etc/nginx
COPY --from=builder /app/build /usr/share/nginx/html
