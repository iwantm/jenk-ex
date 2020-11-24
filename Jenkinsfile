pipeline{
	agent any
	stages{
		stage('Clone Repo'){

			steps{
                    sh label: '', script: '''if [ ! -d "/chaperootodo_client/" ]; then
        									git clone https://gitlab.com/qacdevops/chaperootodo_client.git
											fi'''
                    }

		}
		stage('Install Docker and docker-compose'){
			steps{
				sh 'curl https://get.docker.com | sudo bash'
				sh 'sudo curl -L "https://github.com/docker/compose/releases/download/1.27.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose'
				sh 'sudo chmod +x /usr/local/bin/docker-compose'
			}
			
		}	
		stage('Run App'){
			steps{
				sh 'sudo docker-compose pull && sudo -E DB_PASSWORD=${DB_PASSWORD} docker-compose up -d'
			}
		}

	}
}
