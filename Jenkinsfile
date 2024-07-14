pipeline {
    agent {
        node {
            label 'maven'
        } 
    }
    environment {
        PATH = "/opt/apache-maven-3.9.8/bin:$PATH"
        MAVEN_OPTS = "-Xmx2048m -XX:MaxPermSize=512m"
    }
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/AYUSHUKL/tweet-trend-new.git'
            }
        }
        stage('Build') {
            steps {
                echo "Building code..."
                sh 'mvn clean deploy'
            }
        }
    }
    post {
        always {
            echo "Cleaning up..."
            cleanWs()
        }
        success {
            echo "Build succeeded!"
        }
        failure {
            echo "Build failed. Please check the logs for more details."
            archiveArtifacts artifacts: '**/target/surefire-reports/*.xml', allowEmptyArchive: true
            junit '**/target/surefire-reports/*.xml'
        }
    }
}
