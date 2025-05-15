pipeline {
    agent any

    docker {
        image "maven:3.9.9-jdk"
        label "docker"
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
