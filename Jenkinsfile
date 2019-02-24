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
            usernamePassword(credentialsId: '76e8624f-ea2e-4fab-8337-c57ab7703746', passwordVariable: 'AWS_SECRET', usernameVariable: 'AWS_KEY')
          ]) {
           sh 'packer build -var aws_access_key=${AWS_KEY} -var aws_secret_key=${AWS_SECRET} packer/packer.json'
        }
      }
    }
}
}