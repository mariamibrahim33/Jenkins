pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/mariamibrahim33/SOAPService.git'
                git 'https://github.com/mariamibrahim33/RESTApi.git'
                git 'https://github.com/mariamibrahim33/GrpcService.git'
            }
        }
        stage('Build') {
            steps {
                dir('/Users/mariamibrahim/SOAPService') {
                    sh 'dotnet build SOAPService.sln'
                }
                dir('/Users/mariamibrahim/RESTApi') {
                    sh 'dotnet build RESTApi.sln'
                }
                dir('/Users/mariamibrahim/GrpcService') {
                    sh 'dotnet build GrpcService.sln'
                }
            }
        }
        stage('Test') {
            steps {
                dir('/Users/mariamibrahim/SOAPService') {
                    sh 'dotnet test'
                }
                dir('/Users/mariamibrahim/RESTApi') {
                    sh 'dotnet test'
                }
                dir('/Users/mariamibrahim/GrpcService') {
                    sh 'dotnet test'
                }
            }
        }
        stage('Docker Build') {
            steps {
                dir('/Users/mariamibrahim/SOAPService') {
                    sh 'docker-compose build'
                }
                dir('/Users/mariamibrahim/RESTApi') {
                    sh 'docker-compose build'
                }
                dir('/Users/mariamibrahim/GrpcService') {
                    sh 'docker-compose build'
                }
            }
        }
        stage('Deploy') {
            steps {
                dir('/Users/mariamibrahim/SOAPService') {
                    sh 'docker-compose up -d'
                }
                dir('/Users/mariamibrahim/RESTApi') {
                    sh 'docker-compose up -d'
                }
                dir('/Users/mariamibrahim/GrpcService') {
                    sh 'docker-compose up -d'
                }
            }
        }
    }
}
