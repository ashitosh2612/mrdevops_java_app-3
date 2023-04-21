@Library('jenkins-share-lib') _

pipeline{
    agent any 
    stages{
        stage("Git Checkout"){
            steps{
              
                gitCheckout(
                    branch: "main",
                    url: "https://github.com/ashitosh2612/mrdevops_java_app-3.git"
                )
            }
            
        }
    }
    
}