pipeline {
  agent {
    docker {
	  image 'suryanarayana6/packer_terraform_git_image:firsttry'
    }
  }
  stages {
    stage('Build') {
      steps {
        sh 'npm install'
      }
    }
    stage('Create Packer AMI') {
        steps {
          withCredentials([
            usernamePassword(credentialsId: '1d2e7b3deb2a84686a287994e1c4621c9e176120', passwordVariable: 'AWS_SECRET', usernameVariable: 'AWS_KEY')
          ]) {
           sh 'packer build -var aws_access_key=${AWS_KEY} -var aws_secret_key=${AWS_SECRET} packer/packer.json'
        }
      }
    }
}
}