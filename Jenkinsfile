pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/sanvika15/honorsrepo'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn --version'
                bat 'mvn clean install -DskipTests'
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}
