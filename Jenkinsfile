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
          sh(script: """
              curl -X GET https://${USERNAME}:${PASSWORD}@${ARTIFACTORYURL}/artifactory/maven-central/ -H 'Content-Type: application/json' 
            """ 
        )
        sh(script: """
              curl -X POST https://${USERNAME}:${PASSWORD}@${ARTIFACTORYURL}/artifactory/api/move/maven-central-cache/classworlds?to=/thirdparty-mvn-local/ -H 'Content-Type: application/json' 
            """ 
        )
      }
    }
  }
}
