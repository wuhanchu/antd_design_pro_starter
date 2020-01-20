pipeline {
    agent any
    stages {
        

        stage('Build') { 
            agent {
                docker {
                    image 'node:lts-alpine' 
                    args '-v jenkins-data:/var/jenkins_home -v jenkins_yarn_cache:/Users/wuhanchu/Library/Caches/Yarn' 
                }
            }
            steps{
                sh 'yarn install --registry=https://registry.npm.taobao.org'
                sh 'npm run build'
            }
        }

        stage('Docker Build') {
            steps{
                sh 'docker build . -f ./docker/Dockerfile.hub -t server.aiknown.cn:31003/library/z_antd_design_pro_strater:master' 
            }
        }

        stage('Push') {
            when {
              expression {
                currentBuild.result == null || currentBuild.result == 'SUCCESS' 
              }
            }
            steps {
                sh 'docker push server.aiknown.cn:31003/library/z_antd_design_pro_strater:master'
                sh 'docker rmi server.aiknown.cn:31003/library/z_antd_design_pro_strater:master'
            }
        }

        stage('Deploy') {
            steps{
                sshagent(credentials : ['centos']) {
                    sh "docker pull server.aiknown.cn:31003/library/z_antd_design_pro_strater:master"
                    sh "docker run server.aiknown.cn:31003/z_antd_design_pro_strater -p 8080:80 --name z_antd_design_pro_strater_master z_antd_design_pro_strater:master"
                }
            }
        }
    }
}