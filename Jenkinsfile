pipeline{
    agent any
    stages{
        stage("Pull framework Image"){
            steps{
                    sh "docker pull gowtham415/selenium-docker"
            }
        }
        stage("Start grid"){
            steps{
                sh "docker-compose up -d hub chrome firefox"
            }
        }
        stage("Run test"){
            steps{
                sh "docker-compose up search-module book-flight-module"
            }
        }
    }

    post{
        always{
            archiveArtifacts artifacts: 'output/**'
            sh "docker-compose down"
        }
    }
}