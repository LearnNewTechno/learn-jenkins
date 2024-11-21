pipeline {
    agent {
        label 'AGENT-1'
    }
    options {
        // timeout(time: 10, unit: 'SECONDS') 
        disableConcurrentBuilds()
        retry(1)
    }
    stages {
        stage('Build') {
            steps {
                sh 'echo this is build'  
                // sh 'sleep 10'
                error "faile"
            }
        }
        stage('Test') {
            steps {
                sh 'echo this is Test'  
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo this is Deploy' 
            }
        }
    }
    post {
        always {
            echo "this sections runs always"
            deleteDir()
        }
        success {
            echo "this section run when success"
        }
        failure {
             echo "this section run when failure"
             
        }
    } 
}