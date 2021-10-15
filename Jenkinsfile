node {
    checkout scm
    stage "feching helm repo"
        sh "helm dependency update ./helm"
    stage('Deploy to cluster') {
        sh 'cat "$KUBECONFIG" > /home/ubuntu/.kube/config'
        sh 'helm install microservice-helm ./helm --set microservice-deploys.container.namespace=microservice-ns'
    }
}

