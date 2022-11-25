pipeline {
    agent any
    triggers {
        pollSCM 'H/5 * * * *'
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/eantunez-cheung/epsi-dev709-ci.git'
            }
        }
        stage('clean') {
            steps {
                 sh '''chmod u+x ./mvnw
                    ./mvnw clean'''
            }
        }
        stage('compile') {
            steps {
                 sh '''chmod u+x ./mvnw
                    ./mvnw compile'''
            }
        }
        stage('test') {
            steps {
                 sh '''chmod u+x ./mvnw
                    ./mvnw test'''
            }
        }
        stage('package') {
            steps {
                 sh '''chmod u+x ./mvnw
                    ./mvnw package'''
            }
        }
        stage('archive') {
            steps {
                    sh 'mv target/erphrense-0.0.1-SNAPSHOT.jar target/erphrense-$BUILD_NUMBER.jar'
                    archiveArtifacts artifacts: 'erphrense-*.jar', followSymlinks: false
            }
        }
    }
}
