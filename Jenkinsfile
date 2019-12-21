pipeline {
      agent any
      stages{
         stage("Git Checkout"){
             steps{
               git credentialsId: 'Github-cred', url: 'https://github.com/demodevops2/devopscls14repo.git'
             }
         }
         stage("mvn build"){
             steps{
                 sh "mvn clean package"
                 sh "mv target/*.war target/myweb.war"
             }
         }
         
         stage("deploy-dev"){
            steps{
                sshagent(['tomcat-new']) {
                 sh "sudo scp -o StrictHostKeyChecking=no target/*.war 172.31.8.148:/var/lib/tomcat8/webapps/"
                      
                      
                     
                }
            } 
         } 

      } 
      
}
