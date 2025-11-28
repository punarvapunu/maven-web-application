@Libary("My_shared_library")
pipeline 
{
    agent any

    stages {
        stage('Checkout') {
            steps {
                script {
                    def config = [ 
                            url: 'https://github.com/itdefined-org-apps/node_backend.git',
                            branch: 'main',
                            credentialsId: 'github_token'
                        ]
                    gitCheckout(config)
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
                echo 'Deploying...'
            }
        }
    }
}
