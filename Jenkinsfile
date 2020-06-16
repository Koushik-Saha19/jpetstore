pipeline {
    agent any
    tools {
        maven 'LocalMVN'
        jdk 'LocalJDK'
    }
    stages {
        stage ('Build') {
            steps {
                sh 'mvn clean install' 
            }

        }
        stage ('Deploy') {
            steps {
                sh 'mvn deploy' 
            }
        }
    }
}
