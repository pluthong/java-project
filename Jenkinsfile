properties([pipelineTriggers([githubPush()])]) 

node('linux'){
    stage('Build'){
        git 'https://github.com/pluthong/java-project.git'
        sh "ant -f test.xml -v"
        junit 'reports/result.xml'
    }
}
