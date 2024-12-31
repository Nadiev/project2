pipeline {
    agent any
    
     environment {
        DOCKER_IMAGE = 'project2nadiev:latest'
        CONTAINER_NAME = 'angry_moser'
        PORT_MAPPING = '8089:80'  // Adjust the port mapping as needed
    }
    
    stages {
            stage('Checkout') {
                steps {
                    checkout([$class: 'GitSCM', branches: [[name: 'main']], userRemoteConfigs: [[url: 'https://github.com/Nadiev/project2']]])
                }
            }

            stage('Build Docker Image') {
            steps {
               bat 'docker build -t %DOCKER_IMAGE% .'
            }
        }

        


        stage('Run Docker Container') {
            steps {
                bat 'docker rm -f %CONTAINER_NAME%'
               bat 'docker run -d -p %PORT_MAPPING% --name %CONTAINER_NAME% %DOCKER_IMAGE%'
            }
        }
    }

    
}