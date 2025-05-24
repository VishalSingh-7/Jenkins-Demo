pipeline {
    agent any
    parameters {
        string(name: 'Service_Name', defaultValue: 'AI Service', description: "Enter your Service Name")
        booleanParam(name: 'New_Service', defaultValue: true, description: "")
        choice(name: 'Environment', choices: ['Dev','QA','Staging','Prod' ], description: "")
    }
    stages {
        stage('Run A command') {
            steps {
                sh '''
                ls
                date
                pwd
                '''
                
            }
        }
        stage('Environment Variables') {
            environment {
                username = 'myusername'
            }
            steps {
                sh 'echo  "${BUILD_ID}"'
                sh 'echo  "${Service_Name}"'
                sh 'echo  "${username}"'
            }
        }
        stage('Parameters') {
            steps {
                echo 'deploy on test'
                sh 'echo "${Service_Name}"'
                sh 'echo  "${New_Service}"'
            }
        }
        stage('Continue ?') {
            input {
                message "Should we continue?"
                ok "Yes we Should"
            }
            
            steps {
                echo 'Deploy on Prod.....'
            }
        }
        stage('Deploy on Prod') {
            steps {
                echo 'Deploy on Prod......'
            }
        }
    }
    post{
        always { 
            echo 'I will always say Hello again!'
        }
        failure{
            echo 'Failure'
        }
        success{
            echo 'Successs'
        }
    }
}
