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
                sh 'mvn -DaltDeploymentRepository=libs-snapshot-local::maven-2-default::http://52.142.15.74:8082/artifactory/libs-snaps deploy' 
            }
        }
    }
}
