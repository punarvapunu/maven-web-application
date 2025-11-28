@Library('My_shared_library') _
pipeline 
{
    agent any

    stages {
        stage('Checkout') {
            steps {
                script {
                     echo "========executing A start========"
                     echo "testing"
                    def config = [ 
                            url: 'https://github.com/punarvapunu/maven-web-application.git',
                            branch: 'master',
                            credentialsId: 'github_credatial'
                        ]
                    git_checkout(config)
                    sh '''
                        pwd 
                        ls -lrt
                    '''
                }
                
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying... at end'
            }
        }
    }
}
