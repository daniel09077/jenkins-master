FROM eclipse-temurin:17-jre-alpine

USER root

COPY app.jar /app.jar

# 2. Create a restricted system user named 'appuser'
RUN useradd -r -u 1001 -g root appuser

# 3. Give 'appuser' ownership of the jar file so it has permission to run it
RUN chown appuser /app.jar

# 4. SWITCH USERS: Everything below this line runs as the restricted user
USER appuser

ENTRYPOINT ["java", "-jar", "/app.jar"]
