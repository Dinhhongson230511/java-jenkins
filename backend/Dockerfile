# Chọn image từ OpenJDK
FROM openjdk:11-jre-slim

# Thiết lập thư mục làm việc
WORKDIR /app

# Copy file JAR từ build vào container
COPY target/hello-world-1.0-SNAPSHOT.jar hello-world.jar

# Mở port 8080
EXPOSE 8080

# Chạy ứng dụng
CMD ["java", "-jar", "hello-world.jar"]
