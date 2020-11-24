pipeline{
	agent any
	stages{
		stage('Clone Repo'){

			steps{
                    sh label: '', script: '''if [ ! -d "chaperootodo_client" ]; then
        									git clone https://gitlab.com/qacdevops/chaperootodo_client.git
											fi'''
					
			}

		}
		stage('Install Docker and docker-compose'){
			steps{
                    sh label: '', script: '''
					if [ ! docker ]; then
						curl https://get.docker.com | sudo bash
						sudo curl -L "https://github.com/docker/compose/releases/download/1.27.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/l>        
						sudo chmod +x /usr/local/bin/docker-compose
					elif [ ! docker-compose ]; then
						sudo curl -L "https://github.com/docker/compose/releases/download/1.27.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/l>        
						sudo chmod +x /usr/local/bin/docker-compose
					else
        				echo 'docker and docker compose installed'
					fi'''
					
			}
			
		}	
		stage('Run App'){
			steps{
				sh 'ls'
				sh 'cd chaperootodo_client'
				sh 'ls chaperootodo_client'
				sh 'sudo docker-compose pull && sudo -E DB_PASSWORD=${DB_PASSWORD} docker-compose up -d'
			}
		}

	}
}
