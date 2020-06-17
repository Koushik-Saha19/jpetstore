pipeline {
    agent any
    tools {
        maven 'LocalMVN'
        jdk 'LocalJDK'
    }
    stages {
        stage ('Artifactory configuration') {
            steps {
                rtServer (
                    id: "maven_lib_release_local",
                    url: "http://52.142.15.74:8081/artifactory",
                    username: "admin",
                    password: "jfrog123"

                )

                rtMavenDeployer (
                    id: "MAVEN_DEPLOYER",
                    serverId: "maven_lib_release_local",
                    releaseRepo: "libs-release-local",
                    snapshotRepo: "libs-snapshot-local"
                )
                
            }
        }
        stage ('Exec Maven') {
            steps {
                rtMavenRun (
                    pom: 'pom.xml',
                    goals: 'clean install',
                    deployerId: "MAVEN_DEPLOYER",
                    
                )
            }
        }
        stage ('Download') {
            steps {
                sh "wget --user='admin' --password='jfrog123' 'http://52.142.15.74:8082/artifactory/libs-snapshot/maven-org/mybatis/maven-jpetstore/maven-6.0.2-SNAPSHOT/maven-jpetstore-maven-6.0.2-20200614.151443-15.war'"
            }
        }
  
    }
}
