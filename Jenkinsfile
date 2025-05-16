pipeline {
    agent {
        docker {
            image 'maven:3.9.9-amazoncorretto-21'
            // Don't override working dir; use default (mounted workspace)
            // args '-w /workspace'  // remove this or fix mapping below
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
            // Wrap cleanWs inside node block to provide required context
            script {
                node {
                    cleanWs()
                }
            }
        }
    }
}
