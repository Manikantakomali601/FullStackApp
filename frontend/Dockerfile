#FROM node:18
#WORKDIR /app
#COPY . .
#RUN apt-get update && apt-get install -y xsel
#RUN npm install && npm run build && npm install -g serve
#EXPOSE 3000
#ENTRYPOINT ["serve", "-s", "build", "-l", "3000"]

# ---- Stage 1: Build the React app ----
FROM node:18 AS builder

# Set working directory
WORKDIR /app

# Copy package.json and package-lock.json first (for better caching)
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy rest of the source code
COPY . .

# Build the React app for production
RUN npm run build


# ---- Stage 2: Serve the built app ----
FROM node:18-slim

# Install only what's needed to serve the app
RUN npm install -g serve

# Set working directory
WORKDIR /app

# Copy build output from builder stage
COPY --from=builder /app/build ./build

# Expose port 3000 for the frontend
EXPOSE 3000

# Run the app with serve
CMD ["serve", "-s", "build", "-l", "3000"]

