pipeline {
    agent any
    tools {
        maven 'LocalMVN'
        jdk 'LocalJDK'
    }
    stages {
        stage ('Test and verify') {
            steps {
               sh 'cd ${project.base.directory}'
               sh 'mvn clean verify'
                
            }
        }
   
    }
    post {
        always {
                
                perfReport filterRegex: '', sourceDataFiles: '/var/lib/jenkins/workspace/maven-build-jmeter-test-integration/src/test/resources/test.csv'
               
        }
    }
}
