# Build stage
FROM node:20-alpine AS builder
WORKDIR /app

COPY package*.json ./
RUN npm ci

COPY . .
RUN npm run build

# Production stage
FROM node:20-alpine
WORKDIR /app

COPY --from=builder /app ./

RUN addgroup -S nextjs && adduser -S nextjs -G nextjs
USER nextjs

ENV NODE_ENV=production
EXPOSE 3000

CMD ["npm","start"]