pipeline {
    agent {
        node {
            label 'maven'
        }
    }
environment {
    PATH = "/opt/maven:$PATH"
}
    stages {
        stage('build') {
            steps {
                echo "build code"
                sh 'mvn clean deploy'
            }
        }
    }
}
