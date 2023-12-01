pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }

        stage('Build image') {
            steps{
                script {
                    sh "whoami"
                    sh "pwd"
                    dir('/var/lib/jenkins/services') {
                        sh "pwd"
                        sh "docker build ."
                    }
                }
             }
        }

        stage('Tag to Puch') {
            steps{  
                script {
                    sh "whoami"    
                    sh 'docker login --username thitinon23 --password dckr_pat_bE8dj0znYXToDsHEGTUxhHXIpOQ'
                    sh 'docker tag thitinon23/assignment-mtl thitinon23/assignment-mtl:latest'
                    sh 'docker push thitinon23/assignment-mtl:latest' 
                }
            }
        }
        
    stage('Deploy') {
            steps {
                echo 'Hello Deploy'
                sh "whoami"
                sh "pwd"
                sh "ls -lrt"
                sh "kubectl apply -f ./demo-go.yaml"
            }
        }
        
    stage('Check Pod') {
            steps {
                echo 'Hello Check pod'
                sh "whoami"
                sh "pwd"
                sh "kubectl get pod -n demo-go-ns"
            }
        }
        
    }
    

        

    
}
