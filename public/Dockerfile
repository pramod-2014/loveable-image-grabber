# Stage 1: Build the Vite React App using Bun
FROM node:20 AS builder

WORKDIR /app

# Copy everything to container
COPY . .

# Install deps and build app
RUN npm install
RUN npm run build

# Stage 2: Serve the built files with Nginx
FROM nginx:alpine

# Remove default Nginx static files
RUN rm -rf /usr/share/nginx/html/*

# Copy built files from previous stage
COPY --from=builder /app/dist /usr/share/nginx/html

# Expose port
EXPOSE 80

# Start Nginx server
CMD ["nginx", "-g", "daemon off;"]
