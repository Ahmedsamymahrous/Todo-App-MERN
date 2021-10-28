FROM node:14.16.0-alpine as build-stage

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

RUN npm run build

# EXPOSE 3000

# CMD ["npm", "start"]

# Stage 2
FROM nginx:1.17.0-alpine

COPY --from=build-stage /app/build /usr/share/nginx/html
EXPOSE 80

CMD nginx -g 'daemon off;'