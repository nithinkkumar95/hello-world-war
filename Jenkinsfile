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
		    sh 'cp /opt/jenkins/workspace/Jenkinsjob/target/hello-world-war-1.0.0.war /home/ubuntu/apache-tomcat-10.1.34/webapps'
		} 
	}
   	post {
    success {
        mail to: "nithinkkumar@gmail.com",
             subject: "Jenkins Job Success",
             body: "The Jenkins job completed successfully."
    }
    failure {
        mail to: "nithinkkumar@gmail.com",
             subject: "Jenkins Job Failed",
             body: "The Jenkins job failed. Check the logs for details."
    }
}

	    
    }
}    
