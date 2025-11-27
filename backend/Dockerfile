# Use an official Node.js runtime as the base image
FROM node:18-alpine

# Set the working directory inside the container
WORKDIR /usr/src/app

# Copy package.json and package-lock.json first to leverage Docker cache
COPY package*.json ./

# Install application dependencies
RUN npm install --production

# Copy the rest of the application code
COPY . .

# Expose the port the app runs on (Default for Express is usually 3000 or 5000)
# Make sure this matches the port in your backend code (e.g., server.js)
EXPOSE 8080

# Command to run the application
CMD ["node", "server.js"]