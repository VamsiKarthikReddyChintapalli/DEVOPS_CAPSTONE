# Use an official Node.js runtime as a parent image
FROM node:14-alpine

# Set the working directory to /app
WORKDIR /

# Copy package.json and package-lock.json to the container
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code to the container
COPY . .

# Build the application
RUN npm run build

# Serve the application with a lightweight HTTP server
FROM nginx:alpine
COPY --from=0 /build /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]