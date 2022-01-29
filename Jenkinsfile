node{
    def branchname
    def ApplicationName
    def tool_version
    def environment
    }

pipeline {
        agent none
   
    stages {
           
            stage ('Clean workspace-prior'){
                            agent {label 'master'}
                                            steps {
                                                        cleanWs()
                                                    }
                                    }

stage('Codecheckout') {
                    agent {label 'master'}
                steps{
               checkout changelog: false, poll: false, scm: [$class: 'GitSCM', branches: [[name: '<branchname>']], doGenerateSubmoduleConfigurations: false, extensions: [], gitTool: 'Default', submoduleCfg: [], userRemoteConfigs: [[credentialsId: '<Cred_ID>', url: '<bit bucket URL>']]]
                }
            }

stage('Read Properties') {
                    agent {label 'master'}
              steps{
                   script{
                   def properties = readProperties  file:"${JENKINS_HOME}/workspace/${PropertieFilename}"
                   branchname= properties['branchname']
                   tool_version = properties['tool_version']
                   ApplicationName = properties['ApplicationName']
                   environment = properties['environment']
                  }
                 }
                }
}
}
