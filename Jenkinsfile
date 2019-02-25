pipeline {
    agent { 
		docker 
		{ 
			image 'suryanarayana6/packer_terraform_git_image:firsttry' 
		} 
	}
    environment {
        HOME = '.'
    }

    stages {

        stage('Build') {
            steps {
                sh "npm install"
            }
        }
		
		stage('Create Packer AMI') {
			steps {
				
				withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'a30d892a-be89-45b5-953e-6c42c4a542af', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
				
					sh 'packer build -var aws_access_key=${AWS_ACCESS_KEY_ID} -var aws_secret_key=${AWS_SECRET_ACCESS_KEY} packer/packer.json'
				}

			}
		}
	
    }
}
