pipeline {
  agent any
  environment {
    BRANCH = "${BRANCH_NAME}"
    USERNAME = 'jenkins'
    PASSWORD = 'Admin%401478'
    ARTIFACTORYURL = 'artifactmanager.jfrog.io'
    
  }
  stages {
    stage('Build') {
      when {
          branch 'main'
      }
      steps{
          REMOTEREPONAME = input message: 'Please enter the remote repo name', parameters: [string(defaultValue: '', description: '', name: 'Remote Repository Name')]
          sh(script: """
              curl -X GET https://${USERNAME}:${PASSWORD}@${ARTIFACTORYURL}/artifactory/${REMOTEREPONAME}/ -H 'Content-Type: application/json' 
            """ 
        )
      }
      stage('Prompt for input') {
      when {
          branch 'main'
      }
      steps{
        script{
          REMOTEREPONAME = input message: 'Please enter the remote repo name', parameters: [string(defaultValue: '', description: '', name: 'Remote Repository Name')]
          PACKAGENAME = input message: 'Please enter the package name', parameters: [string(defaultValue: '', description: '', name: 'Package Name')]
          LOCALREPONAME = input message: 'Please enter the local repo name', parameters: [string(defaultValue: '', description: '', name: 'Local Repository Name')]
          sh(script: """
                curl -X POST https://${USERNAME}:${PASSWORD}@${ARTIFACTORYURL}/artifactory/api/move/${REMOTEREPONAME}/${PACKAGENAME}?to=/${LOCALREPONAME}/ -H 'Content-Type: application/json' 
              """ 
          )
        }
      }
    }
  }
}
}
