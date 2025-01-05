pipeline {
    agent any
    //tools {
     //   maven 'Maven-3.4.0' // Specify your Maven version if using Maven
     //   jdk 'JDK11'         // Specify your JDK version
    //}
    environment {
        SONAR_TOKEN = credentials('SONAR_TOKEN') // Store token in Jenkins credentials
    }
    
       stages 
    {
        stage('checkout') {             
            steps {
                sh 'rm -rf hello-world-war'
                sh 'git clone https://github.com/AkshathaMR/hello-world-war/'
            }
        }
         stage('build') { 
            steps {
                sh 'cd hello-world-war'
                sh 'mvn clean package'
            }
        }

        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean install' // Adjust for your build tool
            }
        }
        //add your own sonar account details  
        stage('SonarCloud Analysis') {
            steps {
                withSonarQubeEnv('SonarCloud') {
                    sh '''
                    mvn sonar:sonar \
                      -Dsonar.projectKey=nithinkkumar95 \
                      -Dsonar.organization=nithinkkumar95 \
                      -Dsonar.host.url=https://sonarcloud.io \
                      -Dsonar.login=$SONAR_TOKEN
                    '''
                }
            }
        }
        stage('Quality Gate') {
            steps {
                script {
                    timeout(time: 1, unit: 'MINUTES') {
                        waitForQualityGate abortPipeline: true
                    }
                }
            }
        }
    }
    }
