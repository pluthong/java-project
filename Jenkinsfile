properties([pipelineTriggers([githubPush()])]) 

node('linux'){
    stage('Unit test'){
        git 'https://github.com/pluthong/java-project.git'
        sh "ant -f test.xml -v"
        junit 'reports/result.xml'
    }
    
    stage('Build'){
        sh "ant -f build.xml -v"
    }
    
    stage('Deploy'){
       sh "aws s3 cp /workspace/java-pipeline/dist/rectangle-${currentBuild.number}.jar s3://ust-665-01-paul"
    }
    
    stage('Report'){
       withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: '4ff31954-b0f1-4740-8b76-d6e1dbd9e1b6', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
          sh "aws cloudformation describe-stack-resources --region us-east-1 --stack-name jenkins"
        }
    }

}
