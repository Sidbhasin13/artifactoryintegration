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
                script{
                    REMOTEREPONAME = input message: 'Please enter the remote repo name', parameters: [string(defaultValue: '', description: '', name: 'Remote Repository Name')]
                    PACKAGENAME = input message: 'Please enter the package name', parameters: [string(defaultValue: '', description: '', name: 'Package Name')]
                    sh(script: """
                        curl -X GET https://${USERNAME}:${PASSWORD}@${ARTIFACTORYURL}/artifactory/${REMOTEREPONAME}/${PACKAGENAME}/ -H 'Content-Type: application/json' 
                        """ 
                    )
                }
            }
        }
        stage('Prompt for input') {
            when {
                branch 'main'
            }
            steps{
                script{
                    REMOTEREPONAME = input message: 'Please enter the remote repo name', parameters: [string(defaultValue: '', description: '', name: 'Remote Repository Name')]
                    PACKAGENAME = input message: 'Please enter the package name', parameters: [string(defaultValue: '', description: '', name: 'Package Name')]
                    SUBPACKAGENAME = input message: 'Please enter the sub package name', parameters: [string(defaultValue: '', description: '', name: 'Sub Package Name')]
                    LOCALREPONAME = input message: 'Please enter the local repo name', parameters: [string(defaultValue: '', description: '', name: 'Local Repository Name')]
                    sh(script: """
                            curl -X POST https://${USERNAME}:${PASSWORD}@${ARTIFACTORYURL}/artifactory/api/copy/${REMOTEREPONAME}/${PACKAGENAME}/${SUBPACKAGENAME}?to=/${LOCALREPONAME}/ -H 'Content-Type: application/json' 
                        """ 
                    )
                }
            }
        }
    }
}
