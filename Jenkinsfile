@Library('My_shared_library') _
pipeline 
{
    agent any
     tools {
        maven 'MAVEN'     // same name you set in Global Tool Config
        jdk 'JDK_21'       // same name from Global Tool Config
    }
        environment {
            Image_Name = "maven-web-app"
            REGISTRY = "punarvapunu29/${Image_Name}"
            CONTAINER_NAME = "maven-web-app-container"
            DOCKER_CREDENTAILS = "docker_credendentail"
           // TAG = "${BUILD_NUMBER}"


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
                 sh 'mvn clean install'
                echo "building the code successfully ........."
            }
            
        }
      
        stage('docker build'){
            steps{
                 echo "docker build  started"
                    script{
                     def docker_image  ='docker build -t $REGISTRY:$BUILD_NUMBER .'
                    } 
                   // docker build -t dockerhandson/maven-web-application:1 .
                   //docker build -t $image-name:$BUILD_NUMBER .
                    echo "docker build completed"

                 
            }

        }
         stage('docker push'){
            steps{
                script{
                    docker.withRegistry('https://hub.docker.com', '$DOCKER_CREDENTAILS')
                    docker_image.push()
                }
                
            }
         }
    }
}
