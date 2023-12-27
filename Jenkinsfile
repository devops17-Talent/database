pipeline{
  agent any
  stages{
    stage('connecting to cluster'){
      steps{
      sh 'kubectl config use-context arn:aws:eks:us-west-2:897276212041:cluster/devops-eks-gCFGYxz'
      }
  }
    stage('create db namespace'){
      steps{
    sh 'kubectl create ns devops-database'
    }
    }
  stage('deploy mariadb'){
    steps{
    sh 'helm upgrade --install mariadb --values createat-mariadb.yaml --namespace devops-database '
    }
  }
 stage('pod status'){
   steps{
   sh 'kubectl get pods -n devops-database'
   }
 }
    
}
}
