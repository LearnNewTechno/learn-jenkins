pipeline {
    agent {
        label 'AGENT-1'
    }
    stages {
        stage('Build') {
            steps {
                sh 'echo this is build'  
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
             error "faile"
        }
    } 
}