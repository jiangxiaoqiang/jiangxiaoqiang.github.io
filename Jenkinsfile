pipeline {
    agent { 
        node {
            label 'jenkins-master'
        }
    }

    stages {
       stage('publish') {
            steps{
                sh "git config --global user.email \"jiangtingqiang@gmail.com\""
                sh "git config --global user.name \"jiangxiaoqiang\""
                withCredentials([usernamePassword(credentialsId: 'github-credential', usernameVariable: 'USER', passwordVariable: 'PASS')]) {
                    script {
                        env.encodedPass=URLEncoder.encode(PASS, "UTF-8")
                    }
                    sh 'git add .'
                    sh "git diff-index --quiet HEAD || git commit -m \"[docs] scheduled auto commit task\" || git push"
                    sh "git push origin master"
                } 
            }
        }
    }
}