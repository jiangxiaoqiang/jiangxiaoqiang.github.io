pipeline {
    
    agent { 
        node {
            label 'jenkins-master'
        }
    }

    environment {
        GITHUB_USERNAME     = credentials('github-username')
        GITHUB_PASSWORD = credentials('github-password')
    }

    stages {
        stage('checkout-source') {
            steps {
                git credentialsId: 'gitlab-project-auth',
                url: 'https://github.com/jiangxiaoqiang/xiaoqiang-blog-source.git'
             } 
        }
        
       stage('publish') {
            steps{
                sh "git config --global user.email \"jiangtingqiang@gmail.com\""
                sh "git config --global user.name \"jiangxiaoqiang\""
                sh "git add -A"
                sh "git diff-index --quiet HEAD || git commit -m \"[docs] scheduled auto commit task\" || git push"
                sh "git push https://${GITHUB_USERNAME}:${GITHUB_PASSWORD}@github.com/jiangxiaoqiang/xiaoqiang-blog-source.git"
            }
        }
        
        
    }
}