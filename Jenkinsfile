pipeline {
    agent any
    stages {
        stage("Build Maven") {
            steps {
                sh 'mvn -B clean package'
            }
        }
        stage("Run Gatling") {
            steps {
                sh 'mvn gatling -Dgatling.simulationClass=test.scala -Dgatling.outputDirectory=./report'
            }
            post {
                always {
                    gatlingArchive()
                }
            }
        }
    }
}