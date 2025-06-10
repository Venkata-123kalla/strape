# Use Node 18 Alpine as base image
FROM node:18-alpine

# Set working directory inside the container
WORKDIR /app

# Copy only package.json and package-lock.json (if it exists)
COPY package*.json ./

# Install dependencies (including pg for PostgreSQL)
RUN npm install
RUN npm install pg

# Copy the rest of the application files
COPY . .

# Build the Strapi admin panel
RUN npm run build

# Expose the port Strapi runs on
EXPOSE 1337

# Start Strapi
CMD ["npm", "start"]


