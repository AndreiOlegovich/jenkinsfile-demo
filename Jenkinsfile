pipeline {
    agent { 
        node {
            label 'docker_slave_ssh'
        }
    }
    triggers {
        pollSCM 'H/2 * * * *'
    }
    environment {
        NEW_VERSION = '1.0.0'
    }
    stages {
        stage('Build') {
            steps {
                echo "Building.."
                echo "Building version ${NEW_VERSION}"
                sh '''
                echo "doing build stuff..."
                env
                '''
            }
        }
        stage('Test') {
            when {
                expression { BRANCH_NAME == 'master' || BRANCH_NAME == 'dev' }
            }
            steps {
                echo "Testing.."
                sh '''
                echo "doing test stuff.."
                echo $BRANCH_NAME
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
            echo "Executed no matter what happened in the pipeline."
        }
        success {
            echo "Executed if pipeline was successful."
        }
        failure {
            echo "Executed if pipeline fails."
        }
    }
}
