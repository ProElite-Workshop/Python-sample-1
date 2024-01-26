def img
pipeline {
    environment {
        registry = "ProElite-Workshop/Python-sample-1" //To push an image to Docker Hub, you must first name your local image using your Docker Hub username and the repository name that you created through Docker Hub on the web.
        registryCredential = 'DOCKERHUB'
        githubCredential = 'GITHUB'
        dockerImage = ''
    }
    agent any
    stages {
        
        stage('checkout') {
                steps {
                git branch: 'master',
                //credentialsId: githubCredential,
                url: 'https://github.com/ProElite-Workshop/Python-sample-1.git'
                }
        }
        
        stage ('Test'){
                steps {
                sh "pytest testRoutes.py"
                
             script {
                    echo 'Main Stage 1 - Starting'

                    // Define substages
                    stage('Substage 1.1') {
                        echo 'Executing Substage 1.1'
                    }
                    stage('Substage 1.2') {
                        echo 'Executing Substage 1.2'
                    }

                    echo 'Main Stage 1 - Completed'
                }
                }
        }
        
        stage ('Clean Up'){
            steps{
               // sh returnStatus: true, script: 'docker stop $(docker ps -a | grep ${JOB_NAME} | awk \'{print $1}\')'
               // sh returnStatus: true, script: 'docker rmi $(docker images | grep ${registry} | awk \'{print $3}\') --force' //this will delete all images
               // sh returnStatus: true, script: 'docker rm ${JOB_NAME}'
                 sh 'echo "Clean Up"'
            }
        }

        stage('Build Image') {
            steps {
                script {
                   // img = registry + ":${env.BUILD_ID}"
                   // println ("${img}")
                   // dockerImage = docker.build("${img}")
                    sh 'echo "Build Image"'
                }
            }
        }

        stage('Push To DockerHub') {
            steps {
                script {
                    //docker.withRegistry( 'https://registry.hub.docker.com ', registryCredential ) {
                     //   dockerImage.push()
                    //}
                    sh 'echo "Push To DockerHub"'
                }
            }
        }
                    
        }

    }
