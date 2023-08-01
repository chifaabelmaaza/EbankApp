# Stage 1: Build stage using the Node.js image as a base
FROM node:18.15.0-alpine as build

# Set the working directory inside the container
WORKDIR /app

# Copy the contents of the current directory into the container's working directory (/app/)
COPY ./ /app/

# Install the Node.js dependencies defined in package.json
RUN npm install

# Run the build script defined in package.json to build the application
RUN npm run build

# Stage 2: Final stage using the Nginx image as a base
FROM nginx:latest

# Copy the built application from the previous stage (build stage) to the Nginx default HTML directory
COPY --from=build /app/dist/dash-app /usr/share/nginx/html

# Expose port 80 to allow incoming traffic to the Nginx web server
EXPOSE 80