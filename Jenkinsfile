@Libary("My_shared_library")
pipeline 
{
    agent any

    stages {
        stage('Checkout') {
            steps {
                script {
                     echo "========executing A start========"
                    def config = [ 
                            url: 'https://github.com/punarvapunu/maven-web-application.git',
                            branch: 'master',
                            credentialsId: 'github_credatial'
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
