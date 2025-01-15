pipeline {
    agent any
    
       stages 
    {
        stage('checkout') {             
            steps {
                sh """
                #!/bin/bash
                sleep 10
                
                cd /opt/apache-tomcat-10.1.34/webapps
                ls
                curl -L -u "admin:cmVmdGtuOjAxOjE3Njg0NDk0ODg6cVdjV3NnUlljdGFFNE9aYTRKenh2ZWlrNHFT" -O "http://35.154.69.33:8082/artifactory/hello-world-war-libs-release/com/efsavage/hello-world-war/1.0.16/"
                pwd
                cd /opt/apache-tomcat-10.1.34/bin
                ./shutdown.sh
                sleep 3
                pwd
                
                pwd
                cd /opt/apache-tomcat-10.1.34/bin
                ./startup.sh
                sleep 3
                """ 

            }
        }
         
    }
}
