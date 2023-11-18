pipeline {
    agent any
    
    stages{
        stage ("Build Image"){
            steps {
                script {
                    dockerapp = docker.build("matheusmprado/sampletodoaula3:v${env.BUILD_ID}", '-f ./dockerfile .')
                }
            }
        }
        stage ("Push Image") {
            steps {
                script {
                    docker.withRegistry("https://registry.hub.docker.com",'dockerhub'){
                        dockerapp.push("v${env.BUILD_ID}")
                        dockerapp.push("latest")
                    }
                }
            }
        }
    }
}