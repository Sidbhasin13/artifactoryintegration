pipeline {
  agent any
  environment {
    BRANCH = "${BRANCH_NAME}"
    USERNAME = 'jenkins'
    PASSWORD = 'Admin%401478'
    ARTIFACTORYURL = 'artifactmanager.jfrog.io'
    
  }
  stages {
        stage('Check Dependency in Remote Repository') {
            when {
                branch 'main'
            }
            steps{
                script{
                    //Fetching Details from Remote Cache
                  
                    echo "Please Enter the Remote-Cache Repo Name"
                    REMOTEREPONAME = input message: 'Please enter the remote repo name', parameters: [string(defaultValue: '', description: '', name: 'Remote Repository Name')]
                    echo "Please Enter the Package Name"
                    PACKAGENAME = input message: 'Please enter the package name', parameters: [string(defaultValue: '', description: '', name: 'Package Name')]
                    echo "Please Enter the Sub Package Name"
                    SUBPACKAGENAME = input message: 'Please enter the sub package name', parameters: [string(defaultValue: '', description: '', name: 'Sub Package Name')]
                    sh(script: """
                          curl -X GET https://${USERNAME}:${PASSWORD}@${ARTIFACTORYURL}/artifactory/${REMOTEREPONAME}/${PACKAGENAME}/${SUBPACKAGENAME}/ -H 'Content-Type: application/json' 
                          """ 
                     )
                }
            }
        }
        stage('Fetch Dependency in Remote Cache') {
            when {
                branch 'main'
            }
            steps{
                script{
                    //Fetching Dependencies in Remote Cache from Remote Repository
                    
                    echo "Please Enter the Remote Repo Name"
                    REMOTEREPONAME = input message: 'Please enter the remote repository name', parameters: [string(defaultValue: '', description: '', name: 'Remote Repository Name')]
                    echo "Please Enter the Dependency Path"
                    DEPENDENCYPATH = input message: 'Please enter the dependency path', parameters: [string(defaultValue: '', description: '', name: 'Dependency Path')]                   
                    sh(script: """
                          curl -X GET https://${USERNAME}:${PASSWORD}@${ARTIFACTORYURL}/artifactory/${REMOTEREPONAME}/${DEPENDENCYPATH} -H 'Content-Type: application/json' 
                          """ 
                     )
                }
            }
        }
        stage('Copy from Remote-Cache to Local Repository') {
            when {
                branch 'main'
            }
            steps{
                script{
                    // Copy dependency from Remote-Cache to Local Repository
                    
                    echo "Please Enter the Remote-Cache Repo Name"
                    REMOTEREPONAME = input message: 'Please enter the remote repo name', parameters: [string(defaultValue: '', description: '', name: 'Remote Repository Name')]
//                     echo "Please Enter the Package Name"
//                     PACKAGENAME = input message: 'Please enter the package name', parameters: [string(defaultValue: '', description: '', name: 'Package Name')]
//                     echo "Please Enter the Sub Package Name"
//                     SUBPACKAGENAME = input message: 'Please enter the sub package name', parameters: [string(defaultValue: '', description: '', name: 'Sub Package Name')]
                    echo "Please Enter the Dependency Path"
                    DEPENDENCYPATH = input message: 'Please enter the dependency path', parameters: [string(defaultValue: '', description: '', name: 'Dependency Path')]                   
                    echo "Please Enter the Local Repo Name"
                    LOCALREPONAME = input message: 'Please enter the local repo name', parameters: [string(defaultValue: '', description: '', name: 'Local Repository Name')]
//                     sh(script: """
//                             curl -X POST https://${USERNAME}:${PASSWORD}@${ARTIFACTORYURL}/artifactory/api/copy/${REMOTEREPONAME}/${PACKAGENAME}/${SUBPACKAGENAME}?to=/${LOCALREPONAME}/${PACKAGENAME}/${SUBPACKAGENAME}/ -H 'Content-Type: application/json' 
//                         """ 
//                     )
                    sh(script: """
                              curl -X POST https://${USERNAME}:${PASSWORD}@${ARTIFACTORYURL}/artifactory/api/copy/${REMOTEREPONAME}/${DEPENDENCYPATH}?to=/${LOCALREPONAME}/${DEPENDENCYPATH}/ -H 'Content-Type: application/json' 
                          """ 
                      )
                }
            }
        }
    }
}
