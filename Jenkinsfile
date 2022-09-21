pipeline {
    
    agent {
        label {
            label 'built-in'
        }
    }
    stages {
        stage ('download-22Q2-index-file-on-master'){
		steps {
			dir ("/mnt/projects/22Q2"){
			sh 'rm -rf /mnt/projects/22Q1/project-ashish'
			sh 'git clone --branch 22Q2 https://github.com/ragnar-git/project-ashish.git/22Q2'
			sh 'aws s3 cp /mnt/projects/22Q1/project-ashish/index.html s3://buc-70'
			}
		}
		}
		
		stage ('deploy-on slave-2'){
		agent {
				node {
						label "slave-2"
					}
			}
		steps {
			sh 'sudo aws s3 cp s3://buc-70/index.html /home/ec2-user/index.html'
		}
		}
    }
}
