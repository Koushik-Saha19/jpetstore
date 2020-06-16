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
                    url: "http://52.142.15.74:8082/",
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
                    goals: 'clean install deploy',
                    deployerId: "MAVEN_DEPLOYER"
                )
            }
        }
    }
}
