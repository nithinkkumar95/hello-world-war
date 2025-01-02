pipeline {
       agent {label 'label' }
    stages 
    {
        stage('checkout') {
                steps { 
                sh 'rm -rf hello-world-war'
                sh 'git clone https://github.com/nithinkkumar95/hello-world-war/'
            }
        }
        stage('build') {
                steps {
                    sh 'cd hello-world-war'
                    sh 'mvn clean package'
		}
	}	
        stage('deploy') {
		steps {
		    sh 'cd /opt/jenkins/workspace/Jenkinsjob/target'
		    sh 'scp hello-world-war-1.0.0.war ubuntu@172.31.47.100:/home/ubuntu/apache-tomcat-10.1.34/webapps'
		} 
	}
    }
}    
