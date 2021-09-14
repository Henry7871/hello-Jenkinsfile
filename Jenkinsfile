// original
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
// example 1
pipeline {
    agent any
    environment {
        RELEASE='20.04'
    }
    stages {
        stage('Build') {
            agent any
            environment {
                LOG_LEVEL='INFO'
            }
            steps {
                echo "Building release ${RELEASE} with log level ${LOG_LEVEL}..."
            }
        }
        stage('Test') {
            steps {
                echo "Testing. I can see release ${RELEASE}, but not log level ${LOG_LEVEL}"
            }
        }
    }
}
// example 2
// pipeline {
//    agent any
//     environment {
//       RELEASE='20.04'
//     }
//    stages {
//       stage('Build') {
//             environment {
//                LOG_LEVEL='INFO'
//             }
//             steps {
//                echo "Building release ${RELEASE} with log level ${LOG_LEVEL}..."
//                sh 'chmod +x m2/demo3/build.sh'
//                withCredentials([string(credentialsId: 'an-api-key', variable: 'API_KEY')]) {
//                   sh '''
//                      ./m2/demo3/build.sh
//                   '''
//                }
//             }
//         }
//         stage('Test') {
//             steps {
//                echo "Testing release ${RELEASE}"
//                script {
//                   if (Math.random() > 0.5) {
//                      throw new Exception()
//                   }
//                }
//                writeFile file: 'test-results.txt', text: 'passed'               
//             }
//         }
//    }
//    post {
//       success {
//          archiveArtifacts 'test-results.txt'
//          slackSend channel: '#builds',
//                    color: 'good',
//                    message: "Release ${env.RELEASE}, success: ${currentBuild.fullDisplayName}."
//       }
//       failure {
//          slackSend channel: '#builds',
//                    color: 'danger',
//                    message: "Release ${env.RELEASE}, FAILED: ${currentBuild.fullDisplayName}."
//       }
//    }
// }
// example 3
// pipeline {
//    agent any
   
//    environment {
//        DEMO='1.3'
//    }

//    stages {
//       stage('stage-1') {
//          steps {
//             echo "This is build number $BUILD_NUMBER of demo $DEMO"
//             sh '''
//                echo "Using a multi-line shell step"
//                chmod +x test.sh
//                ./test.sh
//             '''
//          }
//       }
//    }
// }