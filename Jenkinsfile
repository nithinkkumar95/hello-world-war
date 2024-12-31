pipeline {
    agent any
    stages 
    {
        stage('checkout') {
                steps {
                sh 'git clone https://github.com/nithinkkumar95/hello-world-war/'
            }
        }
        stage('build') {
                steps {
                    sh 'cd hello-world-war'
                    sh 'mvn clean package'
            }
        }
    }
}
