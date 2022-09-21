pipeline {
    
    agent {
        label {
            label 'built-in'
        }
    }
    stages {
        stage ('download-22Q3-index-file-on-master'){
		steps {
			dir ("/mnt/projects/22Q3"){
			sh 'rm -rf /mnt/projects/22Q3/project-ashish'
			sh 'git clone --branch 22Q3 https://github.com/ragnar-git/project-ashish.git'
			sh 'aws s3 cp /mnt/projects/22Q3/project-ashish/index.html s3://buc-70/slave-3/'
			}
		}
		}
		
		stage ('deploy-on slave-3'){
		agent {
				node {
						label "slave-3"
					}
			}
		steps {
			sh 'sudo aws s3 cp s3://buc-70/slave-3/index.html /home/ec2-user/index.html'
		}
		}
    }
}
