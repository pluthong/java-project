properties([pipelineTriggers([githubPush()])]) 

node('linux'){
    stage('Build'){
        sh "ant"
    }
}
