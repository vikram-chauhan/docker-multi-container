FROM node:14-alpine as builder
WORKDIR "./app"
COPY ./package.json ./
RUN npm install
COPY . .
RUN npm run build

FROM nginx
EXPOSE 3005
COPY ./nginx/default.conf /etc/nginx/con.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html