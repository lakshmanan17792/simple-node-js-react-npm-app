pipeline {
    agent {
        docker {
            image 'node:6-alpine'
            args '-p 3000:3000'
        }
    }
    environment {
        CI = 'true'
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Run build') {
            steps {
                sh 'npm run build'
            }
        }
        stage('PM2 intallation'){
            steps{
                sh 'npm install pm2 -g'
            }
        }
        stage('Deliver') {
            steps {
                sh 'pm2 start npm -- start'
                // input message: 'Finished using the web site? (Click "Proceed" to continue)'
                // // sh './jenkins/scripts/kill.sh'
            }
        }
    }
}
