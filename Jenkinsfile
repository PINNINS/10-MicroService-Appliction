pipeline {
    agent any
    environment {
        SCANNER_HOME= tool "sonar-scanner"
    }
    stages{
        stage('git checkout'){
            steps{
                git branch: 'main', credentialsId: 'Github', url: 'https://github.com/PINNINS/Projectptyhon-terraform.git'
                
            }
        }
        stage('sonarQube-analysis'){
            steps{
                withSonarQubeEnv('sonar') {
                sh ''' $SCANNER_HOME/bin/sonar-scanner -Dsonar.projectkry=10-tier -Dsonar.projectName=10-Tier -Dsonar.java.binaries=.'''
              }
            }
            stage('adservice'){
            steps{
               script {
                     withDockerRegistery(credentialsId:'docker-cred', toolname:'docker){
                       dir('/var/lib/jenkins/workspaces/10-Tier/src/adservice'){
                       sh 'docker run -t pinnintisrinu/adservice:latest .'
                       sh 'docker push pinnintisrinu/adservice:latest  '
                       sh 'docker rmi pinnintisrinu/adservice:latest '
                  }
                 }
                   
               }
                
            }
        }
        
        stage('cartservice'){
            steps{
               script {
                     withDockerRegistery(credentialsId:'docker-cred', toolname:'docker){
                       dir('/var/lib/jenkins/workspaces/10-Tier/src/cartservice/src'){
                       sh 'docker run -t pinnintisrinu/cartservice:latest .'
                       sh 'docker push pinnintisrinu/cartservice:latest  '
                       sh 'docker rmi pinnintisrinu/cartservice:latest '
                  }
                 }
                   
               }
                
            }
        }
        stage('checkoutservice'){
            steps{
               script {
                     withDockerRegistery(credentialsId:'docker-cred', toolname:'docker){
                       dir('/var/lib/jenkins/workspaces/10-Tier/src/checkoutservice'){
                       sh 'docker run -t pinnintisrinu/chekoutservice:latest .'
                       sh 'docker push pinnintisrinu/checoutservice:latest  '
                       sh 'docker rmi pinnintisrinu/checkouservice:latest '
                  }
                 }
                   
               }
                
            }
        }
         stage('currencyservice'){
            steps{
               script {
                     withDockerRegistery(credentialsId:'docker-cred', toolname:'docker){
                       dir('/var/lib/jenkins/workspaces/10-Tier/src/currencyservice/src'){
                       sh 'docker run -t pinnintisrinu/currencyservice:latest .'
                       sh 'docker push pinnintisrinu/currencyservice:latest  '
                       sh 'docker rmi pinnintisrinu/currencyservice:latest '
                  }
                 }
                   
               }
                
            }
        }
         stage('emailservice'){
            steps{
               script {
                     withDockerRegistery(credentialsId:'docker-cred', toolname:'docker){
                       dir('/var/lib/jenkins/workspaces/10-Tier/src/emailserviceservice/src'){
                       sh 'docker run -t pinnintisrinu/emailserviceservice:latest .'
                       sh 'docker push pinnintisrinu/emailserviceservice:latest  '
                       sh 'docker rmi pinnintisrinu/emailserviceservice:latest '
                  }
                 }
                   
               }
                
            }
        }
        stage('frontend'){
            steps{
               script {
                     withDockerRegistery(credentialsId:'docker-cred', toolname:'docker){
                       dir('/var/lib/jenkins/workspaces/10-Tier/src/frontend'){
                       sh 'docker run -t pinnintisrinu/frontend:latest .'
                       sh 'docker push pinnintisrinu/frontend:latest  '
                       sh 'docker rmi pinnintisrinu/frontend:latest '
                  }
                 }
                   
               }
                
            }
        }
        stage('loadgenerator'){
            steps{
               script {
                     withDockerRegistery(credentialsId:'docker-cred', toolname:'docker){
                       dir('/var/lib/jenkins/workspaces/10-Tier/src/loadgenerator'){
                       sh 'docker run -t pinnintisrinu/loadgenerator:latest .'
                       sh 'docker push pinnintisrinu/loadgenerator:latest  '
                       sh 'docker rmi pinnintisrinu/loadgenerator:latest '
                  }
                 }
                   
               }
                
            }
        }
        stage('paymentservice'){
            steps{
               script {
                     withDockerRegistery(credentialsId:'docker-cred', toolname:'docker){
                       dir('/var/lib/jenkins/workspaces/10-Tier/src/paymentservice'){
                       sh 'docker run -t pinnintisrinu/paymentservice:latest .'
                       sh 'docker push Ppinnintisrinu/paymentservice:latest  '
                       sh 'docker rmi pinnintisrinu/paymentservice:latest '
                  }
                 }
                   
               }
                
            }
        }
       stage('productcatalogservice'){
            steps{
               script {
                     withDockerRegistery(credentialsId:'docker-cred', toolname:'docker){
                       dir('/var/lib/jenkins/workspaces/10-Tier/src/productcatalogservice'){
                       sh 'docker run -t pinnintisrinu/productcatalogservice:latest .' 
                       sh 'docker push pinnintisrinu/productcatalogservice:latest '
                       sh 'docker rmi pinnintisrinu/productcatalogservice:latest '
                  }
                 }
                   
               }
                
            }
        }
        stage('recommendationservice'){
            steps{
               script {
                     withDockerRegistery(credentialsId:'docker-cred', toolname:'docker){
                       dir('/var/lib/jenkins/workspaces/10-Tier/src/recommendationservice'){
                       sh 'docker run -t pinnintisrinu/recommendationservice:latest .'
                       sh 'docker push pinnintisrinu/recommendationservice:latest '
                       sh 'docker rmi pinnintisrinu/recommendationservice:latest'
                  }
                 }
                   
               }
                
            }
        }
        stage('shippingservice'){
            steps{
               script {
                     withDockerRegistery(credentialsId:'docker-cred', toolname:'docker){
                       dir('/var/lib/jenkins/workspaces/10-Tier/src/shippingservice'){
                       sh 'docker run -t pinnintisrinu/shippingservice:latest .'
                       sh 'docker push pinnintisrinu/shippingservice:latest '
                       sh 'docker rmi pinnintisrinu/shippingservice:latest'
                  }
                 }
                   
               }
                
            }
        }

    }
}
