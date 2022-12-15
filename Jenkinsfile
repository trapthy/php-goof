pipeline {
    agent any


    stages {
        stage('Checkout') {
            steps {
                script{
                    checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'git', url: 'https://github.com/trapthy/php-goof.git']]])
                }

            }
        }
        
        stage('Scan') {
            steps{ 
                    snykSecurity ( /* additionalArguments: '--command=python3',*/
                    snykInstallation: 'snyk@latest',
                    snykTokenId: 'c058d01c-fa4f-4572-919a-abb7592ec9d9' ,
                    failOnIssues: 'false')
          
            }   
        }
        // stage('Deploy') {
        //     steps{ 
        //         script{
        //             sh 'pwd'
                   
        //             sh 'python3 main.py'
        //         }
        //     }   
        // }
        
}
}
