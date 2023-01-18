pipeline {
    agent any
    stages {
        stage("Build Maven") {
            steps {
                echo 'Build Maven  '
                sh 'mvn -B clean package'
            }
        }
        stage("Run Gatling") {
            steps {
                sh 'echo run gatling'
                sh 'mvn gatling:test'
            }
            post {
                always {
                    gatlingArchive()
                }
            }
        }
    }
}