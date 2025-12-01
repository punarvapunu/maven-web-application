@Library('My_shared_library') _
pipeline 
{
    agent any
     tools {
        maven 'MAVEN'     // same name you set in Global Tool Config
        jdk 'JDK_21'       // same name from Global Tool Config
    }

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
        stage('build') {
            steps {
                echo 'build...'
                sh 'mvn clean install'
                echo "building"
            }
            
        }
        stage('Deploy') {
            steps {
                echo 'Deploying... at end'
            }
        }
    }
}
