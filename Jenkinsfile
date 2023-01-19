// pipeline {
//     agent any

//     stages {
//         stage('Build') {
//             steps {
//                 echo 'Building..'
//             }
//         }
//         stage('Test') {
//             steps {
//                 echo 'Testing..'
//             }
//         }
//         stage('Deploy') {
//             steps {
//                 echo 'Deploying....'
//             }
//         }
//     }
// }
pipeline {
    agent any
    tools {
        maven 'Maven 3.8.6'
        jdk 'Java 17.0.4.1'
    }
    stages {
        stage("Build Maven") {
            steps{
                withMaven(maven: 'mvn') {
                    echo 'Build Maven  '
                    sh 'mvn --version'
                    sh 'mvn package'
                }
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