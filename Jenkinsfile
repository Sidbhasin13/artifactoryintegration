pipeline {
  agent any
  environment {
    BRANCH = "${BRANCH_NAME}"
    USERNAME = 'admin'
    PASSWORD = 'eyJ2ZXIiOiIyIiwidHlwIjoiSldUIiwiYWxnIjoiUlMyNTYiLCJraWQiOiJzMDVsbElNbm5DZEZYVjJGUEJPNXJRek9TcGN4dGpfOVVrbWg1MXVNeE1vIn0.eyJleHQiOiJ7XCJyZXZvY2FibGVcIjpcInRydWVcIn0iLCJzdWIiOiJqZmFjQDAxZ2Exemg1N2ZxeDN0MXhjMjF0c3kxcDFqXC91c2Vyc1wvYWRtaW4iLCJzY3AiOiJhcHBsaWVkLXBlcm1pc3Npb25zXC9hZG1pbiIsImF1ZCI6IipAKiIsImlzcyI6ImpmZmVAMDAwIiwiZXhwIjoxNjkxODM5MzE4LCJpYXQiOjE2NjAzMDMzMTgsImp0aSI6IjRkZTlhNjdjLWRlNjktNDNiZi1hOGE1LWY0ZjBhNTc0YTI2MSJ9.OZYABR81pZOOPPEsJq_KUdVH2z_B_W1QeCtyzmDnV8nQd_bWzk9NSN6MTUvKxcFoySTg0p7Dtc2UYyK75M0K6NWXZyQPVlu1GR6EntGokKIX2LjY7BzOp4g9nKo8CChlkYBVZ09CIp5gWCPLDriE3hT4s0Kf7n0mDh_JWs1w6AjsI82p9TYwWTrGALmmFEI2v7IcIuExFyEQ2rFUEZzZ0mSn8teZ7g1Ganrs0mUHrF3E1Nw-8-W1LCsiFfUO2AFZ2bDJAWIlOkHU16Gb9RA1muY9m8_JFh0tZBS94kt4LnoXGmZ8bsC4mrTvWnFD5HbxZXQadiAQZgYl85tw9CFWqg'
    ARTIFACTORYURL = '127.0.0.1:8082/ui'
  }
  stages {
    stage('Build') {
      when {
          branch 'main'
      }
      steps{
          sh(script: """
              curl -X PUT https://${USERNAME}:${PASSWORD}@${ARTIFACTORYURL}/api/repositories/dummy-repo -H 'Content-Type: application/json' --data-raw '{"key" : "dummy-repo","type" : "LOCAL","description" : "Local repository for in-house libraries","packageType": "Generic"}'
            """ 
        )
      }
    }
  }
}
