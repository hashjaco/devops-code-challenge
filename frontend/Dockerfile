# Use an official Node.js runtime as the parent image
FROM node:16

WORKDIR /app

COPY package.json yarn.lock ./

RUN yarn install

COPY . .

RUN yarn build

# Serve the build folder on port 3000
FROM node:16-alpine
RUN yarn global add serve
WORKDIR /app
COPY --from=0 /app/build .

EXPOSE 3000

CMD ["serve", "-s", ".", "-l", "3000"]
