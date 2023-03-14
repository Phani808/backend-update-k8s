pipeline {
   agent any

    stages {
        stage('Git Checkout') {
            steps {
            script{
                git branch: 'main', url: 'https://github.com/Phani808/backend-update-k8s.git'  
            }
                }  
            }
           
            stage('Update Manifest'){
            steps {
            script{
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    //withCredentials([gitUsernamePassword(credentialsId: 'github', gitToolName: 'Default')]) {
                   withCredentials([gitUsernamePassword(credentialsId: 'git', gitToolName: 'Default')]) {
                    
                        //def encodedPassword = URLEncoder.encode("$GIT_PASSWORD",'UTF-8')
                        stage('Update Deployment YAML') {
      
        
          def version = '2.1.2' // set the new version here
          
          // Replace the version number in the deployment.yaml file
          sh "sed -i 's/version:.*/version: ${version}/' deployment.yaml"
                        sh "git config --global user.email mpvarma997@gmail.com"
                        sh "git config --global user.name phani"
                        //sh "git switch master"
                        sh "cat deployment.yaml"
                       
                        sh "cat deployment.yaml"
                        sh "git add ."
                        sh "git commit -m 'Done by Jenkins Job changemanifest: $IMAGE_NAME}'"
                        sh "git remote set-url origin https://github.combackend-update-k8s.git"
                        sh 'git push origin HEAD:main'
                        
                        
                    }
                }
            }
        }    
    }      
    }
    }
}   

        
   