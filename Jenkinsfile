pipeline {
    agent { 
        node {
            label 'docker_slave_ssh'
            }
      }
    triggers {
        pollSCM 'H/2 * * * *'
    }
    stages {
        stage('Build') {
            steps {
                echo "Building.."
                sh '''
                echo "doing build stuff.."
                '''
            }
        }
        stage('Test') {
            steps {
                echo "Testing.."
                sh '''
                echo "doing test stuff.."
                '''
            }
        }
        stage('Deliver') {
            steps {
                echo 'Deliver....'
                sh '''
                echo "doing delivery stuff.."
                '''
            }
        }
    }
    post {
        always {
            echo "Executed no matter what happened in pipeline"
        }
        success {
            echo "Executed if pipeline was successful"
        }
        failure {
            echo "Executed if pipeline fails"
        }
    }
}
