FROM node:20-alpine as builder

WORKDIR /app

COPY package.json .
RUN npm i
COPY . .
RUN npm run build

FROM ngnix
EXPOSE 3000
COPY ./nginx/default.conf /etc/ngnix/conf.d/default.conf
COPY --from=builder /app/build /usr/share/ngnix/html
