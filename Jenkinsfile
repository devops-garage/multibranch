// Branch: staging  (copy to repo root as "Jenkinsfile" on the staging branch)
pipeline {
    agent any
    tools { maven 'maven' }
    stages {
        stage('Info') {
            steps { echo "STAGING pipeline - branch: ${env.BRANCH_NAME}" }
        }
        stage('Build & Verify') {
            steps { sh 'mvn -B clean verify' }
        }
        stage('Package') {
            steps { sh 'mvn -B package -DskipTests' }
        }
        stage('Deploy to Staging') {
            steps { echo 'Deploying to STAGING (simulated)...' }
        }
    }
    post {
        always  { junit allowEmptyResults: true, testResults: '**/target/surefire-reports/*.xml' }
        failure { echo 'STAGING build FAILED' }
    }
}
