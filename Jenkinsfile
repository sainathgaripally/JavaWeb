pipeline {
    agent any
    environment {
        sonarrtoken = 'sonartoken'
    }
    stages {
        stage('build package') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Scan code') {
            steps {
                withSonarQubeEnv('sonarqube-6.7.7') {
                    sh 'mvn sonar:sonar'
                }
            }
        }
        stage ('Quality Gate') {
            steps {
                timeout(time: 1, unit: 'HOURS'){
                waitForQualityGate abortPipelie: true
                }
            }
        }
        stage ('testing') {
            steps {
                echo 'completed'
            }
        }
    }
}
