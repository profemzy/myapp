pipeline {
    agent {
        docker {
            image 'node:12-alpine' 
            args '-p 3000:3000' 
        }
    }
    environment {
        HOME = '.'
        CI = 'true'
    }
    stages {

        stage('Build') { 
            steps {
                sh 'npm install' 
            }
        }

         stage('Test') { 
            steps {
                sh 'npm test'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'ansible-playbook /home/opc/play.yml -i /home/opc/hosts'
            }
        }
    }
}
