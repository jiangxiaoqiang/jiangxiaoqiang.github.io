pipeline {
    
    agent { 
        node {
            label 'jenkins-master'
        }
    }

    environment {
        GITHUB_USERNAME     = credentials('github-username')
        GITHUB_PASSWORD     = credentials('github-password')
        GITHUB_PASSWORD1    = credentials('github-password-1')
        df    = credentials('123')
    }

    stages {
        stage('checkout-source') {
            steps {
                git credentialsId: 'gitlab-project-auth',
                url: 'https://github.com/jiangxiaoqiang/jiangxiaoqiang.github.io.git'
             } 
        }
        
       stage('publish') {
            steps{
                sh "git config --global user.email \"jiangtingqiang@gmail.com\""
                sh "git config --global user.name \"jiangxiaoqiang\""
                sh "git add -A"
                sh "git diff-index --quiet HEAD || git commit -m \"[docs] scheduled auto commit task\" || git push"
                sh "echo ${GITHUB_USERNAME}"
                sh "echo ${GITHUB_PASSWORD}"
                sh "echo ${GITHUB_PASSWORD1}"
                sh "echo ${df}"
                sh "git push https://${GITHUB_USERNAME}:${GITHUB_PASSWORD}@github.com/jiangxiaoqiang/jiangxiaoqiang.github.io.git"
            }
        }
        
        
    }
}