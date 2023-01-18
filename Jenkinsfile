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
        maven 'Maven 3.3.9' 
        jdk 'jdk8' 
    }
    stages {
        stage("Build Maven") {
            steps {
                echo 'Build Maven  '
                sh 'mvn --version'
                sh 'mvn package'
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