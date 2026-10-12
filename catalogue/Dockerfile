FROM node:20.20-alpine3.22 as builder
WORKDIR /app
COPY package.json .
COPY *.js .
RUN npm install



FROM node:20.20-alpine3.22
WORKDIR /app
COPY --from=builder /app /app
ENV MONGO="true" \
    MONGO_URL="mongodb://mongodb:27017/catalogue"
CMD ["node", "server.js"]