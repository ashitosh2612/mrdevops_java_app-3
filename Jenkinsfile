@Library('jenkins-share-lib') _

pipeline{
    agent any 

    parameters{
        choice(name: 'action', choices: 'create\ndelete', description: 'choose create/Destroy')

    }
    stages{

        stage("Git Checkout"){
        when { expression { param.action == 'create'} }
            steps{
              
                gitCheckout(
                    branch: "main",
                    url: "https://github.com/ashitosh2612/mrdevops_java_app-3.git"
                )
            }
            
        }

        stage("Unit Test with Mvn"){
             when { expression { param.action == 'create'} }
            steps{
                script{
                    mvnTest()
                }
            }
        }
        stage("Integration Test"){
             when { expression { param.action == 'create'} }
            steps{
                script{
                    mvnintegrationTest()
                }
            }
        }
        stage("static code test by sonarqube"){
              when { expression { param.action == 'create'} }
            steps{
                script{
                    withSonarQubeEnv(credentialsId: 'sonar') {
                          StaticTest()
    
                      }
                }
            }
        }
    }
    
}