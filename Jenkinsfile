pipeline {
    
    agent {
        label {
            label 'built-in'
        }
    }
    stages {
        stage ("deploy-on-slave-1"){
                steps {
                    dir ("/mnt/projects/22Q1"){
                    sh 'rm -rf *'
                    sh 'git clone https://github.com/ragnar-git/project-ashish.git'
                    sh 'scp -i OHIO.pem /mnt/projects/22Q1/project-ashish/index.html ec2-user@18.191.198.253:/home/ec2-user/'
                }
            }
        }
    }
}
