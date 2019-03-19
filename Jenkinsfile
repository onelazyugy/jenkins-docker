pipeline {
  agent {
    node {
      label 'RHEL||master'
    }

  }
  stages {
    stage('PRE-BUILD') {
      steps {
        sh 'echo username: ${USERNAME} pass: ${PASSWORD}'
        echo 'should print already'
      }
    }
    stage('BUILD') {
      steps {
        echo 'building...'
        sh 'mvn clean install -X'
        echo 'building SUCCESS'
      }
    }
    stage('TEST') {
      steps {
        echo 'running test...'
        sh 'mvn test'
      }
    }
    stage('DOCKERIZE') {
      steps {
        echo 'dockerizing...'
        sh 'docker -v'
        sh 'docker build -t jenkins .'
      }
    }
    stage('PUSH TO DOCKERHUB') {
      steps {
        echo 'pushing to dockerhub...'
        sh 'docker login'
        sh 'docker tag jenkins onelazyguy/jenkins:0.0.4-SNAPSHOT'
        sh 'docker image ls'
        sh 'docker push onelazyguy/jenkins:0.0.4-SNAPSHOT'
      }
    }
    stage('DEPLOY APP') {
      steps {
        echo 'deploying app...'
        sh 'docker run -d -p 5001:9002 onelazyguy/jenkins:0.0.4-SNAPSHOT'
      }
    }
  }
  environment {
    USERNAME = "${params.USERNAME}"
    PASSWORD = "${params.PASSWORD}"
  }
  parameters {
    string(name: 'VERSION', defaultValue: 'v0.0.0+00', description: 'The app version being deployed')
    string(name: 'CR', defaultValue: 'CHGXXXXXXX', description: 'The change request number')
    string(name: 'USERNAME', defaultValue: 'username', description: 'Enter user name')
    password(name: 'PASSWORD', defaultValue: 'password', description: 'Enter password')
  }
}