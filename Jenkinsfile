pipeline{
	agent any
	stages{
		stage("Pull Latest Image"){
			steps{
				sh "docker pull vinsdocker/selenium-docker"
			}
		}
		stage("Start Grid"){
			steps{
				sh "docker-compose up -d hub firefox chrome"
			}
		}
		stage("Run Test"){
			steps{
				sh "docker-compose up book-flight-module search-module"
			}
		}
	}
	post{
		always{
			archiveArtifacts artifacts: 'output/**'
			sh "docker-compose down"
			sh "sudo rm -rf output/"
		}
	}
}
