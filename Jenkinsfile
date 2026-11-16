// Branch: dev  (copy to repo root as "Jenkinsfile" on the dev branch)
pipeline {
    agent any
    tools { maven 'maven' }   // name from Manage Jenkins > Tools
    stages {
        stage('Info') {
            steps { echo "DEV pipeline - branch: ${env.BRANCH_NAME}" }
        }
        stage('Compile') {
            steps { sh 'mvn -B clean compile' }
        }
        stage('Test') {
            steps { sh 'mvn -B test' }
        }
    }
    post {
        success { echo 'DEV build OK' }
        failure { echo 'DEV build FAILED' }
    }
}
