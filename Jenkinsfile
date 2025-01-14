pipeline {
    agent any
    tools {
        // Install the Maven version configured as "maven-398" and add it to the path.
        maven "maven-398"
    }
    stages {
        stage('Build') {
            steps {
                // Get some code from a Git repository
                git branch: 'main', url: 'https://github.com/Izzo96/-jenkins-hello-world.git'                // Add other build steps here
                //
                sh "mvn clean package -DskipTests=true" 
            }
        }
        stage('Unit Test') {
            steps {
                sh "mvn test"
            }
        }
        stage('Integration Testing') {
            steps {
                sh "sleep ${params.SLEEP_TIMER}"
                sh """ curl -s http://172.17.0.2:${params.APPLICATION_PORT}/hello | grep -i "Hello, KodeKloud community!" """
        }
}
    }
}
