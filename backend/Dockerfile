FROM node:16-alpine3.17 AS builder

ENV NODE_ENV production
# Add a work directory
WORKDIR /app
# Cache and Install dependencies
COPY package.json .
COPY yarn.lock .

RUN yarn install --production

# Copy app files
COPY . .

RUN yarn build

FROM node:16-alpine3.17 AS production

# Copy bundle from the builder
COPY --from=builder /app/build .

EXPOSE 8080

CMD ["node", "app.js"]