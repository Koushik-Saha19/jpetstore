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
                sh 'curl -T /var/lib/jenkins/workspace/maven-build-jmeter-test-integration/target/jpetstore.war "http://tomcat:tomcat@137.117.85.109:8080/manager/text/deploy?path=/myApp&update=true"'
'
            }
        }
        stage ('Jmeter Test') {
            steps {
               sh 'mvn jmeter:jmeter'
                
            }
        }
   
    }
    post {
        always {
                
                perfReport filterRegex: '', sourceDataFiles: '/var/lib/jenkins/workspace/maven-build-jmeter-test-integration/src/test/resources/test.csv'
               
        }
    }
}
