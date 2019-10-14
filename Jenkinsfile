pipeline {
    agent any 
    stages {
        stage('login-ocpCluster') { 
            steps {
             script {
              sh (script:"oc login -u admin -p ******** --server=https://master.ibmdemo.example.com:8443 --insecure-skip-tls-verify") 
                    }
            }
        }
        stage('create-project') {
         steps {
             script {
              sh (script:"oc project today") 
                }
            }   
        }
        stage('app-deployment') {
            steps {
                script {
                    sh (script:"oc new-app https://github.com/sairbabu58/php-demo.git")
                     }
            }
        }
        stage('routeExpose') {
            steps {
                script {
                    sh (script:"oc expose svc/php-demo --hostname=testapp.cloudapps.ibmdemo.example.com")
                }
            }
        }
    }
}
