FROM node:10.17.0 as build


WORKDIR /app

COPY . .

RUN npm ci --silent
RUN npm run build -- --deployUrl /vehicle-manager/


# Starting nginx
FROM nginx

COPY ./nginx.conf /etc/nginx/nginx.conf

COPY --from=build /app/dist/vehicle-manager /usr/share/nginx/html