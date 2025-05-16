pipeline {
    agent {
        docker {
            image 'maven:3.9.9-amazoncorretto-21'
            args '-u root -w /workspace'
        }
    }

    environment {
        JAVA_TOOL_OPTIONS = '-Duser.home=/var/maven'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/sanvika15/honorsrepo'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn --version'
                sh 'mvn clean install -DskipTests'
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}
