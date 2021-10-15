node {
    checkout scm
    stage "feching helm repo"
        sh "helm dependency update ./helm"
}

  stage('Deploy to cluster') {
    withKubeConfig([credentialsId: 'kubernetes-creds',
                    clusterName: 'tcc-cluster-k8s-admin',
                    namespace: 'microservice-ns'
                    ]) {
      sh 'helm install microservice-helm ./helm --set microservice-deploys.container.namespace=microservice-ns'
    }
  }
