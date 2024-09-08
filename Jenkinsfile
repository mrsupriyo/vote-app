pipeline{
    agent any
    stages{
        stage('BUILDING DOCKER IMAGE'){
            steps {
                sh ''' 
                cd vote
                docker build -t sup0310/capsvote:${BUILD_NUMBER} .
                docker login --username=sup0310 --password=Apple@310
                docker push sup0310/capsvote:v1
                '''
            }
        }
        stage('DEPLOY TO MINIKUBE') {
            steps {
                script{
                    sh '''
                    kubectl set image deployment/vote vote=sup0310/capsvote:${BUILD_NUMBER}
                    '''
                }
            }
        }
    }
}    
