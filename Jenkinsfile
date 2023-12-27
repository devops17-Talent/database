pipeline{
  agent any
  stages{
    stage('connecting to cluster'){
      steps{
      sh 'kubectl config use-context arn:aws:eks:us-west-2:897276212041:cluster/devops-eks-gCFGYxzJ'
      }
  }
    stage('create db namespace'){
      steps{
    sh '''
        myNamespace="database"
       kubectl get namespace | grep -q "^$myNamespace " || kubectl create namespace $myNamespace
         '''
    }
    }
  stage('deploy mariadb'){
    steps{
    sh 'helm upgrade --install mariadb $WORKSPACE --values $WORKSPACE/createat-mariadb.yaml --namespace database '
    }
  }
 stage('pod status'){
   steps{
   sh 'kubectl get pods -n database'
   }
 }
    
}
}
