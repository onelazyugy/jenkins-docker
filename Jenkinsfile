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
        stage('BUILD') {
            steps {
                echo 'building...'
                sh 'pwd'
            }

        }
        stage('DOCKERIZE') {
            steps {
                echo 'dockerizing...'
                sh 'docker -v'
            }
        }
    }
}