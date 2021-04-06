pipeline {
    agent {
        label 'docker-agent'
    }
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
    }
}
 
 

