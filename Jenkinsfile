pipeline {
    agent any
    environment {
        PROJECT_ID = 'wn-cloud-275704'
		CLUSTER_NAME = 'wn-cloud-portal-qa'
		LOCATION = 'us-central1-c'
		CREDENTIALS_ID = 'gke'
    }
    stages {
        stage("Checkout code") {
            steps {
                checkout scm
            }
        }      
        stage('Deploy to GKE') {
            steps{
                //sh "sed -i 's/hello:latest/hello:${env.BUILD_ID}/g' deployment.yaml"
                step([$class: 'KubernetesEngineBuilder', projectId: env.PROJECT_ID, clusterName: env.CLUSTER_NAME, location: env.LOCATION, manifestPattern: 'deployment.yaml', credentialsId: env.CREDENTIALS_ID, verifyDeployments: true])
            }
        }
    }    
}
