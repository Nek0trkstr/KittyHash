FROM node:alpine as builder
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build

FROM nginx:1.27.2-alpine
COPY nginx.conf /etc/nginx/nginx.conf
COPY --from=builder /app/build /var/www
EXPOSE 80
ENTRYPOINT ["nginx","-g","daemon off;"]