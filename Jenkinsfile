properties([pipelineTriggers([githubPush()])]) 

node('linux'){
    stage('Build'){
        sh "ant -f build.xml -v"
    }
}
