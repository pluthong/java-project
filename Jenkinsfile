
properties([pipelineTriggers([githubPush()])]) 

node('linux'){
    
    stage('Unit Tests'){
        sh "ant -f test.xml -v"
        junit 'reports/result.xml'
    }
    
}
