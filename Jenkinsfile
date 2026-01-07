pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                echo 'Packaging application...'
                sh 'mvn package'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                sh 'scp target/myapp.war user@server:/deployments/'
            }
        }

        stage('Notify') {
            steps {
                echo 'Notifying team...'
                slackSend(channel: '#devops', message: 'Build and deployment complete!')
            }
        }
    }
}
