node {
    checkout scm
    stage "feching helm repo"
        sh "helm dependency update ./helm"
    stage('Deploy to cluster') {
        withCredentials([kubeconfigContent(credentialsId: 'kubernetes-creds', variable: 'KUBECONFIG_CONTENT')]) {
            sh 'cat "$KUBECONFIG_CONTENT" > ~/.kube/config'
            sh 'helm install microservice-helm ./helm --set microservice-deploys.container.namespace=microservice-ns'
        }
    }
}

