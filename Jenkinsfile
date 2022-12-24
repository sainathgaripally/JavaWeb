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
                    sh 'mv sonar:sonar'
                }
            }
        }
    }
}
