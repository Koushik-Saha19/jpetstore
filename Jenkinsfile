pipeline {
    agent any
    tools {
        maven 'LocalMVN'
        jdk 'LocalJDK'
    }
    stages {
        stage ('Test and verify') {
            steps {
               sh 'mvn jmeter:jmeter'
                
            }
        }
   
    }
}
