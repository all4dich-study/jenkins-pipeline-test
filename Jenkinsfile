import jenkins.model.*
//import hudson.*

// get current thread / Executor
//def thr = Thread.currentThread()
// get current build
//def build = thr?.executable

node('master'){
    stage("Get Each Node's label"){
        Jenkins.instance.nodes?.each {
            println "${it.labelString}"
        }
        sh 'ls'
    }
    
    stage("Get All labels"){
        Jenkins.instance.labels?.each {
            println "${it.name}"
        }
    }
}
