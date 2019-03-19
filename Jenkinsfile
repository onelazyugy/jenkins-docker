#!/usr/bin/env groovy

pipeline {
    agent { node { label 'RHEL||master' } }
    parameters {
        string(name: 'VERSION', defaultValue: "v0.0.0+00", description: 'The app version being deployed')
        string(name: 'CR', defaultValue: "CHGXXXXXXX", description: 'The change request number')
        string(name: 'CF_USERNAME', defaultValue: "", description: 'The cloud foundry user that will be used to approve and deploy')
        password(name: 'CF_PASSWORD', defaultValue: "", description: 'The cloud foundry password')
        string(name: 'CF_USERNAME2', defaultValue: "", description: 'The 2nd cloud foundry user that will be used to approve the deployment')
        password(name: 'CF_PASSWORD2', defaultValue: "", description: 'The 2nd cloud foundry deployment user password.')
    }

    environment {
        ARTIFACTORY_TOKEN=credentials('artifactory-token')
        QUALITYHUB_TOKEN=credentials('ps-giftcardmanager-quality-hub-token')
        TRACKER_TOKEN=credentials('tracker-token')
        GITHUB_TOKEN=credentials('github-token')
        VERSION="${params.VERSION}"
        CF_USERNAME="${params.CF_USERNAME}"
        CF_PASSWORD="${params.CF_PASSWORD}"
        CF_USERNAME2="${params.CF_USERNAME2}"
        CF_PASSWORD2="${params.CF_PASSWORD2}"
        CHG_REQUEST="${params.CR}"
        ENVIRONMENT="production"
        QUALITYHUB_ENVIRONMENT="production"
        QUALITYHUB_APP_KEY="ps-giftcardmanager"
        QUALITYHUB = "scripts/quality-hub.sh"
        STAGING_DIRECTORY="fordeployment"
    }

    stages {
        stage('BUILD') {
            steps {
                echo 'building...'
            }

        }
        stage('DOCKERIZE') {
            steps {
                echo 'dockerizing...'
            }
        }
    }
}