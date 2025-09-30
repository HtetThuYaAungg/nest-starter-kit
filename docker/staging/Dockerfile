
FROM node:24.4.1-alpine3.22


WORKDIR /usr/src/app

# Set timezone (UTC+6:30)
RUN apk add --no-cache tzdata \
  && cp /usr/share/zoneinfo/Asia/Yangon /etc/localtime \
  && echo "Asia/Yangon" > /etc/timezone

# Install required dependencies for Prisma
RUN apk add --no-cache openssl

# Install dependencies
COPY package*.json ./
RUN npm install && npm cache clean --force

# Copy Prisma schema and generate client
COPY prisma ./prisma
RUN npx prisma generate

# Copy all other source files
COPY . .

# Build app
RUN npm run build

# Remove dev dependencies
RUN npm prune --production

EXPOSE 3002

CMD sh -c "npx prisma migrate deploy && npm run seed && npm run start:prod"