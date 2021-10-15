node {
    checkout scm
    stage "feching helm repo"
        sh "helm dependency update ./helm"
    stage('Deploy to cluster') {
        withCredentials([kubeconfigContent(credentialsId: 'kubernetes-creds', variable: 'KUBECONFIG_CONTENT')]) {
            sh '''echo "$KUBECONFIG_CONTENT" > kubeconfig'''
            sh 'export KUBECONFIG=./kubeconfig'
            sh 'helm install microservice-helm ./helm --set microservice-deploys.container.namespace=microservice-ns'
        }
    }
}

