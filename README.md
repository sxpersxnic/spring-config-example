# spring-config-example

## application.yml
```yml
spring:
  application:
    name: application-name
  main:
    allow-bean-definition-overriding: true  # Allow bean overriding
  profiles:
    active: dev  # Active profile (e.g., dev, prod)

server:
  port: 8080  # HTTP server port
  servlet:
    context-path: /api  # Base path for the application
  compression:
    enabled: true
    mime-types: text/html, text/xml, application/json
    min-response-size: 1024
  datasource:
    url: jdbc:postgresql://localhost:5432/my_database
    username: db_user
    password: db_password
    driver-class-name: org.postgresql.Driver
  jpa:
    hibernate:
      ddl-auto: update  # Schema management: update, validate, create, etc.
    show-sql: true  # Enable SQL logging
    properties:
      hibernate:
        format_sql: true  # Pretty-print SQL

  security:
    user:
      name: admin  # Default username
      password: secret  # Default password
    oauth2:
      resourceserver:
        jwt:
          issuer-uri: https://issuer.example.com  # JWT issuer URI

logging:
  level:
    root: INFO
    com.example: DEBUG  # Enable DEBUG logs for a specific package
  file:
    name: logs/app.log  # Path to log file
  pattern:
    console: "%d{yyyy-MM-dd HH:mm:ss} - %msg%n"  # Console log format
    file: "%d{yyyy-MM-dd HH:mm:ss} [%thread] %-5level %logger{36} - %msg%n"  # File log format

  thymeleaf:
    prefix: classpath:/templates/
    suffix: .html
    cache: false  # Disable caching for development
    mode: HTML
  cache:
    type: redis  # Supported: simple, concurrent, jcache, caffeine, redis, etc.
  redis:
    host: localhost
    port: 6379
    password: secret

  servlet:
    multipart:
      max-file-size: 10MB
      max-request-size: 10MB

mail:
    host: smtp.gmail.com
    port: 587
    username: your-email@gmail.com
    password: your-email-password
    protocol: smtp
    properties:
      mail:
        smtp:
          auth: true
          starttls:
            enable: true

messages:
    basename: messages  # Location of message files
    encoding: UTF-8

management:
  endpoints:
    web:
      exposure:
        include: "*"  # Expose all actuator endpoints
  endpoint:
    health:
      show-details: always  # Show health details

app:
  name: My Custom App
  feature:
    enabled: true
    max-users: 100

config:
    import: optional:file:/path/to/external-config.yml
```
