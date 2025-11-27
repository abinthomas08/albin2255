# --- Stage 1: Build the Angular Application ---
FROM node:18-alpine AS build

WORKDIR /app

# Copy dependency definitions
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the source code
COPY . .

# Build the Angular app for production
# Check your package.json script; usually it's "build"
RUN npm run build -- --configuration production

# --- Stage 2: Serve with Nginx ---
FROM nginx:alpine

# Copy the built artifacts from Stage 1 to the Nginx html directory
# NOTE: Replace 'mean-app-frontend' below with the actual name of your project 
# found in your angular.json file under "outputPath" or "dist/project-name"
COPY --from=build /app/dist/angular-15-crud /usr/share/nginx/html

# Expose port 80 for the Nginx container
EXPOSE 80

# Start Nginx
CMD ["nginx", "-g", "daemon off;"]