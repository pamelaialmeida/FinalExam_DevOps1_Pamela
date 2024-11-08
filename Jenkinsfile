pipeline{
    agent {
        docker {
            image 'node:18.17.1-alpine3.18'
        }
    }

    environment {
    FIREBASE_DEPLOY_TOKEN = credentials('firebase-token')
    }

    stages{
        stage('Building'){
            steps{
                echo 'Installing Firebase tools'
                sh 'npm install -g firebase-tools'
            }
        } 

         stage('Testing'){
            steps{
                echo 'Deploying the project to Firebase (Test environment) automatically using a Webhook'
                sh 'firebase deploy -P finalexam-testing-pamela --token "$FIREBASE_DEPLOY_TOKEN"'
            }
        }

        stage('Staging'){
            steps{
                echo 'Deploying the project to Firebase (Staging environment) automatically using a Webhook'
                sh 'firebase deploy -P finalexam-staging-pamela --token "$FIREBASE_DEPLOY_TOKEN"'
            }
        }

        stage('Production'){
            steps{
                echo 'Deploying the project to Firebase (Production environment) automatically using a Webhook'
                sh 'firebase deploy -P finalexam-production-pamela --token "$FIREBASE_DEPLOY_TOKEN"'
            }
        }
    }
}