pipeline {
    agent any
        stages {
            stage('Build') {
                agent {
                    docker { image 'gradle:7.5.1-jdk11' }
                }
                    steps {
                        sh 'gradle build'
                        archiveArtifacts artifacts: 'build/libs/labgradle-*-SNAPSHOT.jar', fingerprint: true
                    }
            }
            stage('Test') {
                agent {
                    docker { image 'gradle:7.5.1-jdk11' }
                }
                    steps {
                        sh 'gradle test'
                        junit 'build/test-results/test/TEST-*.xml'
                    }
            }
    }
}
