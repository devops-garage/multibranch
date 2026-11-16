// Branch: main / prod  (copy to repo root as "Jenkinsfile" on the prod branch)
pipeline {
    agent any
    tools { maven 'maven' }
    options {
        timeout(time: 30, unit: 'MINUTES')
        disableConcurrentBuilds()
    }
    stages {
        stage('Info') {
            steps { echo "PROD pipeline - branch: ${env.BRANCH_NAME}" }
        }
        stage('Build & Test') {
            steps { sh 'mvn -B clean verify' }
        }
        stage('Approval') {
            steps {
                input message: 'Deploy to PRODUCTION?', ok: 'Deploy'
            }
        }
        stage('Deploy to Prod') {
            steps { echo 'Deploying to PRODUCTION (simulated)...' }
        }
    }
    post {
        success { echo 'PROD deploy OK' }
        failure { echo 'PROD deploy FAILED' }
    }
}
