# Sample Spring boot with Maven, Docker and Jenkins with blue ocean plugin
# Prerequisite
- must have Docker, Jenkins with blue ocean installed locally
- must have a dockerhub account to push and store docker images
- run Jenkins locally, I have my setup as <code>https://localhost:9090</code>

# How To
- in pom.xml, define whatever <code>\<version>0.0.x-SNAPSHOT\</version></code>
- in Dockerfile, make sure version match <code>ARG JAR_FILE=target/jenkins-0.0.x-SNAPSHOT.jar</code>
- in Jenkinsfile, make sure <code>sh docker run -d -p 5001:9002 onelazyguy/jenkins:0.0.x-SNAPSHOT</code>
- run the app from the docker image: <code>docker run -d -p 5001:9002 onelazyguy/jenkins:0.0.x-SNAPSHOT</code>
- *note:* <code>9002</code> is the port defined in the application.property, if you want to change it, make sure you update the port above to match