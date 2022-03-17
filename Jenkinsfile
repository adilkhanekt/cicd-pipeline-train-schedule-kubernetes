pipeline {
    agent any
    environment {
        //Simplified pipeline to test deploying docker image to Kubernetes cluster using Jenkins
        DOCKER_IMAGE_NAME = "adilkhanekt/train_schedule_node_js"
    }
    stages {
        stage('DeployToProduction') {
            when {
                branch 'master'
            }
            steps {
                input 'Deploy to Production?'
                milestone(1)
                kubernetesDeploy(
                    kubeconfigId: 'kube_creds',
                    configs: 'train-schedule-kube.yaml',
                    enableConfigSubstitution: true
                )
            }
        }
    }
}