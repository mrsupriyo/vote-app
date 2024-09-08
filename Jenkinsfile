pipeline{
    agent any
    stages{
        stage('BUILDING DOCKER IMAGE'){
            steps {
                sh ''' 
                cd vote
                docker build -t sup0310/capstone:v1 .
                docker login --username=sup0310 --password=Apple@310
                docker push sup0310/capsvote:v1
                '''
            }
        }
    }
    stage('DEPLOY TO MINIKUBE') {
        steps {
            script{
                sh '''
                cd k8s-specifications
                kubectl apply -f deployment.yaml
                kubectl apply -f ingress.yaml
                '''
            }
        }
    }
}
