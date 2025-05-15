pipeline {
    environment {
        JAVA_TOOL_OPTIONS = "-Duser.home=/var/maven"
    }
    agent 
    docker {
        image "maven:3.9.9-jdk"
        label "docker"
        args "-v /tmp/maven:/var/maven/.m2 -e MAVEN_CONFIG-/var/maven/.m2"
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
