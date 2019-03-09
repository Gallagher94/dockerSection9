FROM node:alpine as builder
WORKDIR '/app'
COPY ./package.json .
RUN npm install
COPY . . 
RUN npm run build



#We need an nginx server to serve up our react assets. This server will listen on port 30000

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY  --from=builder /app/build /usr/share/nginx/html