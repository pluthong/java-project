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

}
