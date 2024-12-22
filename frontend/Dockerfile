# docker file for the production    example for the production
# In this file we are copying only build folder to nginx container as its the webserver
# as on prod we will not need any other folder
# this is a multi stage docker file from one temporary container we are copying build folder from the 
# first container to the other container
FROM node:16-alpine as builder
WORKDIR "/app"
COPY package.json .
RUN npm install
COPY . .
RUN npm run build

FROM nginx 
COPY --from=builder /app/build /usr/share/nginx/html


##  How to run this
# docker run -it -p 8080:80 <image_id>.
