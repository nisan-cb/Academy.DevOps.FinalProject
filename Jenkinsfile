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
                sh 'mvn gatling:test -Dgatling.simulationClass=test.scala -Dgatling.outputDirectory=reports'
            }
            post {
                always {
                    gatlingArchive()
                }
            }
        }
    }
}