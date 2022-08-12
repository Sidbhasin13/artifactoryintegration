pipeline {
  agent any
  environment {
    BRANCH = "${BRANCH_NAME}"
    USERNAME = 'admin'
    PASSWORD = '%40%24ID%26bHA786'
    ARTIFACTORYURL = 'localhost:8082/ui'
  }
  stages {
    stage('Build') {
      when {
          branch 'main'
      }
      steps{
          sh(script: """
              curl -X PUT https://${USERNAME}:${PASSWORD}@${JIRAURL}/api/repositories/dummy-repo -H 'Content-Type: application/json' --data-raw '{"key" : "dummy-repo","type" : "LOCAL","description" : "Local repository for in-house libraries","packageType": "Generic"}'
            """ 
        )
      }
    }
  }
}
