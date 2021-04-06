pipeline {
    agent {
        label 'docker-agent'
    }
    //tools {nodejs "nodejs"}
    stages {
        stage('Clone source code') {
            steps {
                git 'https://github.com/huanhpp/nodejs-test.git'
            }
        }
        stage ('Cài đặt dependencies của app'){
            steps {
                sh 'npm install'
            }
        }
        stage ('Khởi động app'){
           steps {
               sh 'nohup node index.js &'
           }
        }
        stage ('Chạy script kiểm thử'){
          steps {
              sh 'npm test'
          }
        }
        stage ('Chạy Junit'){
         steps {
                junit 'test.xml'
            }
        }
    }
    post {
        always {
            echo 'One way or another, I have finished'
            //deleteDir() /* clean up our workspace */
        }
        success {
            echo 'I succeeded!'
            emailext body: 'ok!', subject: 'nodejs-test', to: 'trunghuan@gmail.com'
        }
        unstable {
            echo 'I am unstable :/'
        }
        failure {
            echo 'I failed :('
        }
        changed {
            echo 'Things were different before...'
        }
    }
}
 
 

