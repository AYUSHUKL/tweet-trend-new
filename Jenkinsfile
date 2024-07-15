pipeline {
    agent {
        node {
            label 'maven'
        } 
    }
environment {
    PATH = "/opt/apache-maven-3.9.8/bin:$PATH"
}
    stages {
        stage('build') {
            steps {
                echo "build code"
                sh 'mvn clean'
            }
        }
    }
}
