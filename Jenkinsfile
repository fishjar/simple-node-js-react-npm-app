// pipeline {
//     agent {
//         docker {
//             image 'node:6-alpine'
//             args '-p 3000:3000'
//         }
//     }
//     environment {
//         CI = 'true'
//     }
//     stages {
//         stage('Build') {
//             steps {
//                 sh 'npm install'
//             }
//         }
//         // stage('Test') {
//         //     steps {
//         //         sh './jenkins/scripts/test.sh'
//         //     }
//         // }
//         // stage('Deliver') {
//         //     steps {
//         //         sh './jenkins/scripts/deliver.sh'
//         //         input message: 'Finished using the web site? (Click "Proceed" to continue)'
//         //         sh './jenkins/scripts/kill.sh'
//         //     }
//         // }
//     }
// }

// pipeline {
//     agent {
//         docker {
//             image 'docker'
//             args '-v /var/run/docker.sock:/var/run/docker.sock'
//         }
//     }

//     stages {
//         sh 'docker run hello-world'
//     }
// }

pipeline {
    agent {
        docker {
            image 'docker'
            args '-v /var/run/docker.sock:/var/run/docker.sock'
        }
    }
    environment {
        CI = 'true'
    }
    stages {
        stage('Build') {
            steps {
                sh 'docker run hello-world'
            }
        }
        // stage('Test') {
        //     steps {
        //         sh './jenkins/scripts/test.sh'
        //     }
        // }
        // stage('Deliver') {
        //     steps {
        //         sh './jenkins/scripts/deliver.sh'
        //         input message: 'Finished using the web site? (Click "Proceed" to continue)'
        //         sh './jenkins/scripts/kill.sh'
        //     }
        // }
    }
}