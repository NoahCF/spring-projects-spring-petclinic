pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh './mvnw clean' 
            }
        }
        stage('Test') {
            steps {
                sh './mvnw test' 
            }
        }
        stage('Package') {
            steps {
                sh './mvnw package' 
            }
        }
       stage('Deploy') {
            when {
                branch 'master'
            }
            steps {
                sh './mvnw deploy' 
            }
        }
         stage('Slack Notification') {
            steps {
                slackSend "Build Succeeded - ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)"
            }
        }
    }
}
