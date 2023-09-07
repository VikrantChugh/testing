pipeline {
    agent any
   
    
    
    stages {
        stage('checkout') {
            steps {
               checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/VikrantChugh/testing.git']])
            }
        }
        stage('credential') {
            steps {
                withCredentials([[
                    $class: 'AmazonWebServicesCredentialsBinding',
                    credentialsId: "aws-jenkins-2",
                    accessKeyVariable: 'AWS_ACCESS_KEY_ID',
                    secretKeyVariable: 'AWS_SECRET_ACCESS_KEY'
]]) {
            }
      }
        }
        
    stage ("terraform init") {
            steps {
                sh 'terraform init -reconfigure '
                
            }
        }
        stage ("terraform plan") {
            steps {
                sh 'terraform plan '
            }
        }
        // stage ("terraform apply") {
        //     steps {
        //         sh 'terraform ${action} --auto-approve '
        //     }
        // }
        
    }  
}
