node {
    checkout scm
    stage "Deploy to cluster"
        sh "helm dependency update ./helm"
        sh "helm install microservice-helm ./helm --set microservice-deploys.container.namespace=microservice-ns"
}
