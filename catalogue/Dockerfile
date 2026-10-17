FROM node:20.20-alpine3.22 AS builder
WORKDIR /app
COPY package.json .
COPY *.js .
RUN npm install


FROM node:20.20-alpine3.22
WORKDIR /app
EXPOSE 8080
COPY --from=builder /app /app
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop && \
    chown -R roboshop:roboshop /app
USER roboshop
# Managing env variables in k8s
# ENV MONGO="true" \
#     MONGO_URL="mongodb://mongodb:27017/catalogue"
CMD ["server.js"]
ENTRYPOINT ["node"]


# FROM node:20
# WORKDIR /app
# COPY package.json .
# COPY *.js .
# RUN npm install
# ENV MONGO="true" \
#     MONGO_URL="mongodb://mongodb:27017/catalogue"
# CMD ["node", "server.js"]