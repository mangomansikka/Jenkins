pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/mangomansikka/Jenkins'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install -U'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Code Coverage') {
            steps {
                jacoco execPattern: '**/target/jacoco.exec'
            }
        }
    }

    post {
        always {
            junit '**/target/surefire-reports/*.xml'
            jacoco execPattern: '**/target/jacoco.exec'
        }
    }
}
