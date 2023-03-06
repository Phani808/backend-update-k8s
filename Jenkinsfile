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
                options {
    timeout(time: 30, unit: 'MINUTES')
}
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    //withCredentials([gitUsernamePassword(credentialsId: 'github', gitToolName: 'Default')]) {
                  withCredentials([usernamePassword(credentialsId: 'git', passwordVariable: 'git pass', usernameVariable: 'git user')]) {
                    
                        //def encodedPassword = URLEncoder.encode("$GIT_PASSWORD",'UTF-8')
                        sh "git config --global user.email mpvarma997@gmail.com"
                        sh "git config --global user.name phani"
                        //sh "git switch master"
                        sh "cat deployment.yaml"
                        sh "sed -i 's+34.125.107.168:8083/backend.*+34.125.107.168:8083/backend:${DOCKERTAG}+g' deployment.yaml"
                        sh "cat deployment.yaml"
                        sh "git add ."
                        sh "git commit -m 'Done by Jenkins Job changemanifest: ${env.BUILD_NUMBER}'"
                        sh "git push --force https://${git user}:${git pass}@github.com/${git user}/backend-update-k8s.git' HEAD:main"
                        
                        
                    }
                }
            }
        }    
    }      
    }
  
   }

        
   