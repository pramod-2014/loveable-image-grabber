# ------------ Stage 1: Build the app ------------
FROM node:18-alpine AS builder

# Set working directory
WORKDIR /app

# Copy only package files first for caching
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the source code
COPY . .

# Build the app
RUN npm run build

# ------------ Stage 2: Run the app ------------
FROM node:18-alpine AS production

# Set working directory
WORKDIR /app

# Only copy the built app and production dependencies
COPY --from=builder /app/package*.json ./
COPY --from=builder /app/node_modules ./node_modules
COPY --from=builder /app/dist ./dist  # Assuming build output goes to "dist"

# Expose port (change if needed)
EXPOSE 3000

# Start the app
CMD ["node", "dist/index.js"]  # Change the path as per your app's entry point

