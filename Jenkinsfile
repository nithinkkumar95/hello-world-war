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
			     echo "pipeline success"
				 mail (
				       to: 'nithinkkumar@gmail.com'
					   subject: "job is success:  ${env.JOB_NAME} - ${env.BUILD_NUMBER}",
					   body: "the build is succees for ${env.JOB_NAME} - Build #${env.BUILD_NUMBER} was successfull. \n\n" +
                             "view the details here:${env.Build_URL}"
                ) 							 						
        }
		failure {
		    echo 'pipeline is failed. please check the logs.'
			mail (
				       to: 'nithinkkumar@gmail.com'
					   subject: "job is failed:  ${env.JOB_NAME} - ${env.BUILD_NUMBER}",
					   body: "the build is failed for ${env.JOB_NAME} - Build #${env.BUILD_NUMBER} was successfull. \n\n" +
                             "view the details here:${env.Build_URL}"
							 )
    }
}

	    
    }
}    
