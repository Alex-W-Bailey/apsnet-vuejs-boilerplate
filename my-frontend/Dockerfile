# Build stage
FROM node:20-alpine AS build
WORKDIR /app

# Copy package files and install
COPY package*.json ./
RUN npm install

# Copy rest of frontend and build
COPY . .
RUN npm run build

# Production stage (nginx serves static files)
FROM nginx:alpine
COPY --from=build /app/dist /usr/share/nginx/html
EXPOSE 80
