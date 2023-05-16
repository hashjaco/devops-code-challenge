# Use an official Node runtime as the parent image
FROM node:latest

# Set the working directory in the container to /app
WORKDIR /app

# Copy package.json and package-lock.json to the working directory
COPY package.json yarn.lock ./

# Install any needed packages specified in package.json
RUN yarn install

# Bundle app source inside Docker image
COPY . .

# Make port 8080 available to the outside of the Docker container
EXPOSE 8080

# Run app.js using node when the container launches
CMD [ "node", "index.js" ]
