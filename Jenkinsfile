pipeline {
   agent any
   environment {
        APP_NAME = "backend"
        IMAGE_TAG = "${BUILD_NUMBER}"
        

    }

    stages {
        stage('Git Checkout') {
            steps {
            script{
                git branch: 'main', url: 'https://github.com/Phani808/backend-update-k8s.git'  
            }
                }  
            }
           
            stage('Updating kubernetes deployment file') {
            steps{
            script {
                sh """
                cat deployment.yml
                sed -i 's/${APP_NAME}.*/${APP_NAME}:${IMAGE_VERSION}/g' deployment.yml
                cat deployment.yml
                """
        }
   
    }
} 
//  stage('Git Version Update') {
            // steps {
                // script {
                    // withCredentials([gitUsernamePassword(credentialsId: 'git', gitToolName: 'Default')]) {
                    //     sh 'git config --global user.email "mpvarma997@gmail.com"'
                    //     sh 'git config --global user.name "phani"'
                    //     sh "git remote set-url origin https://github.com/Phani808/backend.git"
                    //     sh 'git add .'
                    //     sh 'git commit -m "update deployment.yml file"'
                    //     sh 'git push origin HEAD:main'
                    // }
                }
            }


        
   