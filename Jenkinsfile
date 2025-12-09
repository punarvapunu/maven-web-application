@Library('My_shared_library') _
pipeline 
{
    agent any
     tools {
        maven 'MAVEN'     // same name you set in Global Tool Config
        jdk 'JDK_21'       // same name from Global Tool Config
    }
        environment {
            image-name : "maven-web-app"
            registry : "punarvapunu29/${image-name}"


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
                            credentialsId: 'github'
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
                 sh 'mvn clean'
                echo "building the code successfully."
            }
            
        }
      
        stage('docker build'){
            steps{
                 echo "docker build  started"
                    sh 'docker build -t $registry:$BUILD_NUMBER .'
                   // docker build -t dockerhandson/maven-web-application:1 .
                   //docker build -t $image-name:$BUILD_NUMBER .
                    echo "docker build completed"

                 
            }

        }
        
    }
}
