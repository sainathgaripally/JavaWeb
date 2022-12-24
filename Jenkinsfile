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
        stage('Quality gates') {
            steps {
                timeout(time: 1, unit: 'HOURS') {
                    def st = waitForQualityGate()
                    if (st.status != 'OK') {
                        error "pipeline aborted : ${st.status}"
                    }
                }
            }
        }
    }
}
