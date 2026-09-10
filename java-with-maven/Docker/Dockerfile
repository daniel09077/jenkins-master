#Step 1: Grab the official Maven binaries
FROM maven:3.9.6-eclipse-temurin-17-alpine AS maven-source
# Step 2: Use the official Jenkins Inbound Agent as the base
FROM jenkins/inbound-agent:latest-jdk21
# Step 3: Switch to root to configure the container system
USER root
# Step 4: Copy Maven configuration and binaries from stage 1
COPY --from=maven-source /usr/share/maven /usr/share/maven
#COPY --from=maven-source /usr/bin/mvn /usr/bin/mvn
# Step 5: Create a symlink so 'mvn' is universally available
RUN ln -s /usr/share/maven/bin/mvn /usr/bin/mvn
# Step 6: Revert back to the default jenkins user for security
USER jenkins