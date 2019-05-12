properties([pipelineTriggers([githubPush()])]) 

node('linux'){
    
    stage('Build'){
        sh "ant -f build.xml -v"
    }
    
    stage('Deploy'){
       sh "aws s3 cp /workspace/java-pipeline/dist/rectangle-${currentBuild.number}.jar s3://ust-665-01-paul"
    }

    stage('Report'){
        withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: '0aa4642c-4306-49e8-bf3c-9ad7c44546ca', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
          sh "aws cloudformation describe-stack-resources --region us-east-1 --stack-name jenkins"
        }
    }
    
}
