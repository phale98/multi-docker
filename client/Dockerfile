# Tag phase as builder
FROM node:alpine AS builder

# Change working directory of the container
WORKDIR '/app'

COPY ./package.json ./

RUN npm install

COPY . .

RUN npm run build

# This will place the build folder in /app/build

# Using a second from statment automatically terminates
# the previous phase builder. 
FROM nginx

EXPOSE 3000

COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf

# Destination is nginx specific, contents are automatically
# served up by nginx.

COPY --from=builder /app/build /usr/share/nginx/html

# Don't need to start up nginx as that is the defualt command
# for the nginx container.



