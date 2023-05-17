FROM node:16-alpine3.17 AS builder

ENV NODE_ENV production

WORKDIR /app

COPY package.json yarn.lock ./

RUN yarn install --production

COPY . .

RUN yarn build

# Bundle static assets using nginx for better performance
FROM nginx:1.24.0-alpine3.17 AS production
ENV NODE_ENV production

COPY --from=builder /app/build /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
