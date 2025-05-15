pipeline {
    agent {
        docker {
            image 'maven:3.9.9-eclipse-temurin'
            label 'docker'
            args '-v /tmp/maven:/var/maven/.m2 -e MAVEN_CONFIG=/var/maven/.m2'
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
