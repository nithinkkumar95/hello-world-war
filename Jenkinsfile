pipeline {
    parameters {
        string(name: 'cmd', defaultValue: 'package', description: 'Who should I say hello to?')

        choice(name: 'ch', choices: ['One', 'Two', 'Three'], description: 'Pick something')

           }
    agent {label 'slave1' }
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
                    sh 'mvn clean $cmd'
            }
        }
    }
}
