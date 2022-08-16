pipeline {
  agent any
  environment {
    BRANCH = "${BRANCH_NAME}"
    USERNAME = 'jenkins'
    PASSWORD = 'Admin%401478'
    ARTIFACTORYURL = 'artifactmanager.jfrog.io'
    PACKAGENAME = ''
    REMOTEREPONAME = ''
    LOCALREPONAME = ''
  }
  stages {
    stage('Build') {
      when {
          branch 'main'
      }
      steps{
          sh(script: """
              curl -X GET https://${USERNAME}:${PASSWORD}@${ARTIFACTORYURL}/artifactory/maven-central/ -H 'Content-Type: application/json' 
            """ 
        )
        sh(script: """
              curl -X POST https://${USERNAME}:${PASSWORD}@${ARTIFACTORYURL}/artifactory/api/move/${REMOTEREPONAME}/${PACKAGENAME}?to=/${LOCALREPONAME}/ -H 'Content-Type: application/json' 
            """ 
        )
      }
    }
  }
}
