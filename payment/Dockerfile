# FROM python:3.9.25-alpine3.22 as builder
# WORKDIR /app
# COPY *.py .
# COPY payment.ini .
# COPY requirements.txt .
# RUN pip3 install -r requirements.txt


# FROM python:3.9.25-alpine3.22
# WORKDIR /app
# EXPOSE 8080
# COPY --from=builder /app /app
# RUN addgroup -S roboshop && adduser -S roboshop -G roboshop && \
#     chown -R roboshop:roboshop /app
# USER roboshop
# # Managing env variables in k8s
# ENV CART_HOST="cart" \
#     CART_PORT="8080" \
#     USER_HOST="user" \
#     USER_PORT="8080" \
#     AMQP_HOST="rabbitmq" \
#     AMQP_USER="roboshop" \
#     AMQP_PASS="roboshop123"
# CMD ["uwsgi", "--ini", "payment.ini"]


FROM python:3.9
WORKDIR /app
COPY *.py .
COPY payment.ini .
COPY requirements.txt .
RUN pip3 install -r requirements.txt
ENV CART_HOST="cart" \
    CART_PORT="8080" \
    USER_HOST="user" \
    USER_PORT="8080" \
    AMQP_HOST="rabbitmq" \
    AMQP_USER="roboshop" \
    AMQP_PASS="roboshop123"
CMD ["uwsgi", "--ini", "payment.ini"]