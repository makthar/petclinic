pipeline {
	agent any
    stages {
        stage('Build on k8 ') {
            steps { 
		    withCredentials([[
    $class: 'AmazonWebServicesCredentialsBinding',
    credentialsId: "aws-eks-credentials",
    accessKeyVariable: 'AWS_ACCESS_KEY_ID',
    secretKeyVariable: 'AWS_SECRET_ACCESS_KEY'
]]) 
		    {
                        sh 'pwd'
                        sh 'cp -R helm/* .'
		        sh 'ls -ltr'
                        sh 'pwd'
                        sh '/usr/local/bin/helm upgrade --install petclinic-app petclinic  --set image.repository=registry.hub.docker.com/makthar/petclinic --set image.tag=5 --kubeconfig ~/.kube/config'
		    }		
            }           
        }
    }
}
