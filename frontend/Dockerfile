# Use lightweight Node image
FROM node:20-alpine

# Create working directory
WORKDIR /app

# Copy dependency files
COPY package.json package-lock.json* ./

# Install dependencies
RUN npm install

# Copy application source
COPY . .

# Build Next.js application
RUN npm run build

# Expose application port
EXPOSE 3000

ENV NEXT_PUBLIC_API_URL=http://backend:8000

# Start Next.js server
CMD ["npm", "start"]