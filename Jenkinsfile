pipeline {
    agent any
    environment {
        sonarrtoken = 'sonartoken'
    }
    stages {
        stage('Scan code') {
            steps {
                withSonarQubeEnv('sonarqube-6.7.7') {
                    sh 'mvn sonar:sonar'
                }
            }
        }
        stage('build package') {
            steps {
                sh 'mvn clean package'
            }
        }
    }
}
