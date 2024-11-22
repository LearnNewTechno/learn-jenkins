pipeline {
    agent {
        label 'AGENT-1'
    }
    options {
        // timeout(time: 10, unit: 'SECONDS') 
        disableConcurrentBuilds()
        retry(2)
    }
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }
    stages {
        stage('Build') {
            steps {
                sh 'echo this is build'  
                // sh 'sleep 10'
            }
        }
        stage('Test') {
            steps {
                echo "this is Test :::: ${env.GIT_BRANCH}" 
            }
        }
        stage('Deploy') {
            when {
                allOf {
                    branch 'main'
                }
            }
            steps {
                sh 'echo this is Deploy' 
            }
        }
        stage ('print params') {
            steps {
                echo "Hello : ${params.PERSON}"
                echo "Biography : ${params.BIOGRAPHY}"
                echo "Toggle : ${params.TOGGLE}"
                echo "Choice :  ${params.CHOICE}"
                echo "Password : ${params.PASSWORD}"
            }
        }
        // stage('Approval') {
        //     input {
        //         message "Should we continue?"
        //         ok "Yes, we should."
        //         submitter "alice,bob"
        //         parameters {
        //             string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        //         }
        //     }
        //     steps {
        //         echo "Hello, ${PERSON}, nice to meet you."
        //     }
        // }
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