FROM node:10.17.0 as build


WORKDIR /app

COPY . .

RUN npm ci --silent
RUN npm run build -- --deployUrl /driver-manager/


# Starting nginx
FROM nginx

COPY ./nginx.conf /etc/nginx/nginx.conf

COPY --from=build /app/dist/driver-manager /usr/share/nginx/html