
# # Use the Jenkins image as the base image
# FROM jenkins/jenkins:lts

# # Switch to root user to install dependencies
# USER root

# # Install prerequisites and Docker client (use Debian package for reliability)
# RUN apt-get update -y && \
#     apt-get install -y --no-install-recommends apt-transport-https ca-certificates curl gnupg docker.io && \
#     apt-get clean && rm -rf /var/lib/apt/lists/*

# # Install/upgrade required Jenkins plugins at build time
# # Copy a plugins list and use the bundled plugin CLI to install versions
# COPY plugins.txt /usr/share/jenkins/ref/plugins.txt
# RUN jenkins-plugin-cli -f /usr/share/jenkins/ref/plugins.txt || true

# # Add Jenkins user to the Docker group (create if it doesn't exist)
# RUN groupadd -f docker && \
#     usermod -aG docker jenkins

# # Create the Docker directory and volume for DinD
# RUN mkdir -p /var/lib/docker
# VOLUME /var/lib/docker

# # Switch back to the Jenkins user
# USER jenkins



FROM jenkins/jenkins:lts

USER root

RUN apt-get update && \
    apt-get install -y docker.io && \
    rm -rf /var/lib/apt/lists/*

RUN groupadd -f docker && \
    usermod -aG docker jenkins

USER jenkins