node {
    stage('Checkout') {
        checkout([$class: 'GitSCM',
        branches: [[name: '*/main']],
        extensions: [],
        userRemoteConfigs: [[credentialsId: 'git',
        url: 'https://github.com/DobreMihai-echo/long-covid-web-infrastructure']]])
    }
    stage('Deploy') {
        step([$class: 'KubernetesEngineBuilder',
             projectId: env.PROJECT_ID,
             clusterName: env.CLUSTER,
             location: env.ZONE,
             manifestPattern: 'k8s/',
             credentialsId: env.PROJECT_ID,
             verifyDeployments: true])
    }
}