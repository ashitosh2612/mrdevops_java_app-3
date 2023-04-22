@Library('jenkins-share-lib') _

pipeline{
    agent any 

    parameters{
        choice(name: 'action', choices: 'create\ndelete', description: 'choose create/Destroy')
        string(name: 'ImageName', description: 'Name of docker build',    defaultValue: 'javaapp')
        string(name: 'ImageTag',  description: 'tag of docker build',     defaultValue: 'v1')
        string(name: 'AppName',   description: 'name of the application', defaultValue: 'springboot')

    }
    stages{

        stage("Git Checkout"){
        when { expression { params.action == 'create'} }
            steps{
              
                gitCheckout(
                    branch: "main",
                    url: "https://github.com/ashitosh2612/mrdevops_java_app-3.git"
                )
            }
            
        }

        // stage("Unit Test with Mvn"){
        //      when { expression { params.action == 'create'} }
        //     steps{
        //         script{
        //             mvnTest()
        //         }
        //     }
        // }
        // stage("Integration Test"){
        //      when { expression { params.action == 'create'} }
        //     steps{
        //         script{
        //             mvnintegrationTest()
        //         }
        //     }
        // }
        // stage("static code test by sonarqube"){
        //       when { expression { params.action == 'create'} }
        //     steps{
        //         script{
        //            def sonarcredentialsId = 'sonar'
        //                   StaticTest(sonarcredentialsId)
    
                      
        //         }
        //     }
        // }
        //  stage("quality gate status check sonarqube"){
        //       when { expression { params.action == 'create'} }
        //     steps{
        //         script{
        //            def gatecredentialsId = 'sonar'
        //                   StaticTest(gatecredentialsId)
    
                      
        //         }
        //     }
        // }
        //   stage("maven package build"){
        //      when { expression { params.action == 'create'} }
        //     steps{
        //         script{
        //         Packagebuild()
        //         }
        //     }
        // }
        stage("docker image build"){
             when { expression { params.action == 'create'} }
             steps{
                script{
                    Dockerbuild("${params.ImageName}", "${params.ImageTag}", "${params.AppName}")
                }
             }

        }
    }
    
}