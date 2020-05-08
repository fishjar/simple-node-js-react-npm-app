pipeline {
    agent {
        // docker {
        //     image 'node:6-alpine'
        //     args '-p 3000:3000'
        // }
        docker 'node:6-alpine'
    }
    environment {
        CI = 'true'
    }
    stages {
        // stage('Example') {
        //     steps {
        //         echo "-------WORKSPACE-------->: ${WORKSPACE}"
        //     }
        // }
        // stage('Install') {
        //     steps {
        //         // sh 'npm install --registry https://registry.npm.taobao.org'
        //         sh 'npm install'
        //     }
        // }
        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }
        stage('Deploy dev') {
            agent any
            when {
                branch 'dev'
            }
            steps {
                // sh """
                //     echo "Deploy dev"
                // """
                echo "----WORKSPACE----: ${WORKSPACE}"
                sshagent(credentials : ['583a9537-f155-4cbd-b8ad-103ab53eed0c']) {
                    sh "scp -r ${WORKSPACE}/build root@192.168.1.36:/data/tmp/build/dev"
                }
            }
        }
        stage('Deploy product') {
            when {
                branch 'product'
            }
            steps {
                sh """
                    echo "Deploy product"
                """
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
    post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }
}
