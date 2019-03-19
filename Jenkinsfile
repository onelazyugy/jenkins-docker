#!/usr/bin/env groovy

pipeline {
    agent { node { label 'RHEL||master' } }
    parameters {
        string(name: 'VERSION', defaultValue: "v0.0.0+00", description: 'The app version being deployed')
        string(name: 'CR', defaultValue: "CHGXXXXXXX", description: 'The change request number')
        string(name: 'USERNAME', defaultValue: "username", description: 'Enter user name')
        password(name: 'PASSWORD', defaultValue: "password", description: 'Enter password')
    }

    environment {
        USERNAME="${params.USERNAME}"
        PASSWORD="${params.PASSWORD}"
    }

    stages {
        stage('PRE-BUILD') {
            steps {
                echo 'what is USERNAME?'
                sh 'echo ${USERNAME}'
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
            }
        }
        stage('PUSH TO DOCKERHUB') {
            steps {
                echo 'pushing to dockerhub...'
                sh 'docker login'
                sh 'docker tag docker-demo onelazyguy/docker-springboot-demo:0.0.3-SNAPSHOT'
                sh 'docker image ls'
                sh 'docker push onelazyguy/docker-springboot-demo:0.0.3-SNAPSHOT'
            }
        }
    }
}