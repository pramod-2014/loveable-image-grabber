FROM node:18-alpine AS builder

WORKDIR /app

# 👇 Step 1: Copy only package.json and package-lock.json first
COPY package.json package-lock.json ./

# 👇 Step 2: Install dependencies
RUN npm install

# 👇 Step 3: Copy rest of the source code
COPY . .

# 👇 Step 4: Build the app
RUN npm run build
