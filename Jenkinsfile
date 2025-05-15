pipeline {
    agent any

    tools {
        maven "3.9.9"
    }

    stages {
        stage('Checkout') {
            steps {
                 git branch: 'main', url: 'https://github.com/sanvika15/honorsrepo'
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
