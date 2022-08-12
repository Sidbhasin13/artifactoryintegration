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
              curl -X POST https://${USERNAME}:${PASSWORD}@${ARTIFACTORYURL}/api/repositories/dummy-repo -H 'Content-Type: application/json' --data-raw '{"key" : "dummy-repo","type" : "LOCAL","description" : "Local repository for in-house libraries","packageType": "Generic"}'
            """ 
        )
      }
    }
  }
}
