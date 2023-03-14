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
                        sh "git config --global user.email mpvarma997@gmail.com"
                        sh "git config --global user.name phani"
                        //sh "git switch master"
                        sh "cat deployment.yaml"
                        sh "sed -i 's+34.125.107.168:8083/backend.*+34.125.107.168:8083/backend:${env.IMAGE_NAME}+g' deployment.yaml"
                        sh "cat deployment.yaml"
                        sh "git add ."
                        sh "git commit -m 'Done by Jenkins Job changemanifest: ${env.IMAGE_NAME}}'"
                        sh "git remote set-url origin https://github.combackend-update-k8s.git"
                        sh 'git push origin HEAD:main'
                        
                        
                    }
                }
            }
        }    
    }      
    }
  
   }

        
   