FROM maven:3.9.14 as builder
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN mvn clean package \
    mv target/shipping-1.0.jar shipping.jar 


FROM eclipse-temurin:17-jre-alpine
WORKDIR /app
EXPOSE 8080
COPY --from=builder /app/shipping.jar .
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop && \
    chown -R roboshop:roboshop /app
USER roboshop
# Managing env variables in k8s
ENV CART_ENDPOINT="cart:8080" \
    DB_HOST="mysql"
CMD ["java", "-jar", "shipping.jar"]


# FROM maven:3.9.14
# WORKDIR /app
# COPY pom.xml .
# COPY src ./src
# RUN mvn clean package
# RUN mv target/shipping-1.0.jar shipping.jar 
# ENV CART_ENDPOINT="cart:8080" \
#     DB_HOST="mysql"
# CMD ["java", "-jar", "shipping.jar"]