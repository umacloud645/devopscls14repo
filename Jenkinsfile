pipeline {
          agent any
          stages{
              stage("SCM"){
                  steps{
                      git credentialsId: 'github-cred', url: 'https://github.com/demodevops2/devopscls14repo.git'
                  }
              }
              
                  stage("Build and compile"){
                  steps{
                      sh "mvn clean package"
                      sh "mv target/*.war target/myweb.war"
                  }
              }
              
                stage("Deploy war file"){
                  steps{
                      sshagent(['tomcat-new']) {
                        sh "scp -o StrictHostKeyChecking=no target/myweb.war ubuntu@172.31.13.77:/var/lib/tomcat8/webapps"
                      }
                  }
              }
          }
          
}  

