pipeline{
    agent any
    stages{
        stage("checkout"){
            steps{
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/anjali3soni/cloudfront-practice.git']])
            }
            
        }
        stage("s3")
        {   steps{
                withCredentials([aws(accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'aws-creds', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY')]){
                    sh 'aws s3 cp ./index.html s3://cloud.anjalisoni.in.net/'
                    sh 'aws s3 cp ./style.css s3://cloud.anjalisoni.in.net/'
                }
            }
            
        }
    }
}