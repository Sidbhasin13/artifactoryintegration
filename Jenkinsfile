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
              curl -X GET https://${USERNAME}:${PASSWORD}@${ARTIFACTORYURL}/api/repositories/dummy-repo -H 'Content-Type: application/json' 
            """ 
        )
      }
    }
  }
}
