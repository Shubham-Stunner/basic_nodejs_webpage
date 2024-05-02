pipeline {
    agent any
    
    tools{
        nodejs 'nodejs-1'
    }

    stages {
        stage('GIT CHECKOUT') {
            steps {
                git branch: 'main', changelog: false, poll: false, url: 'https://github.com/Shubham-Stunner/basic_nodejs_webpage.git'
            }
        }
        
        stage('Intall Dependencies') {
            steps {
               sh "npm install"
            }
        }
        
        stage('OWASP Dependency Check') {
            steps {
               dependencyCheck additionalArguments: '--scan ./', odcInstallation: 'dc'
                dependencyCheckPublisher pattern: '**/dependency-check-report.xml'
            }
        }
        
        stage('Docker build and Push') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-new', toolName: 'docker') {
                        sh "docker build -t demonodejs ."
                        sh "docker tag demonodejs stunnershubham/nodejs:latest"
                        sh "docker push stunnershubham/nodejs:latest"
    
                    }
                }
               
            }
        }
        
        stage('Docker Deploy') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-new', toolName: 'docker') {
                        sh "docker run -d --name latestnode -p 8081:8081 stunnershubham/nodejs:latest"
    
                    }
                }
               
            }
        }
    }
}
