pipeline{
	agent any
	tools{
		maven 'Maven'
	}
	stages{
		stage('CheckOut'){
			steps{
				git branch:'master', url:'https://github.com/varshitha5111/ansibleExternal.git'
			}
		}
		stage('Build'){
			steps{
				sh 'mvn clean package'
			}
		}
		stage('archive'){
			steps{
				archiveArtifacts artifacts:'target/*war',fingerprint:true
			}
		}
		stage('deploy'){
			steps{
				sh 'mvn clean package'
				sh 'ansible-playbook ansible/playbook.yml -i ansible/hosts.ini'
			}
		}
	}
}
