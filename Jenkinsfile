pipeline {
  agent any
  environment {
    BRANCH = "${BRANCH_NAME}"
    USERNAME = 'admin'
    PASSWORD = 'eyJ2ZXIiOiIyIiwidHlwIjoiSldUIiwiYWxnIjoiUlMyNTYiLCJraWQiOiJTQ280Zy1PNTdyY1ZJTHN5QlRVODcxRzhMMmRNMlk0RmFHTU9lRG16WWwwIn0.eyJleHQiOiJ7XCJyZXZvY2FibGVcIjpcInRydWVcIn0iLCJzdWIiOiJqZmFjQDAxZzk1NTgwYnYzcmoyMW5ubmowajkxanc4XC91c2Vyc1wvYWRtaW4iLCJzY3AiOiJhcHBsaWVkLXBlcm1pc3Npb25zXC9hZG1pbiIsImF1ZCI6IipAKiIsImlzcyI6ImpmZmVAMDAwIiwiZXhwIjoxNjkxODQwMzI4LCJpYXQiOjE2NjAzMDQzMjgsImp0aSI6ImIwYThhZTU5LTNhYTAtNDgzMS1hMWFiLTU3NzM4MTU5MzQxZCJ9.RSnzfdv_NPwFFAhJgGZonctpECclSGAaHoqX991oMMlmaqsu35Gszttmui6I8-Elg8DzM_UJDqP1SMCHi_jIybl9u84q6CC5boEJZEWcR534VSM1xKUTXlr2GeHukrMoPpqc9lLTga7vJ1E-wPBYbpr2kNAT9G6oRLNBx0nCdtcWDHK2SUp4mKt-w4H-m9Te7NViFcXKpFIbIyS-LFDJS9xeFIFXnAqm5TODo0v8NXbOpdaJA63l1xWg6lfv-pz4SxKYfAlHjTmwRGx_Zst2JMzndA5Vb0B-agJ2XEHUJ-geUHBiSiKGSRLZ-c_aUlbTtv7hytnUDBL5S-Yw0If7xA'
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
