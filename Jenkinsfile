pipeline{
    agent{ label "OI_GradleBuild_App"}
    environment{
        VERSION = "${env.BUILD_ID}"
    }
    stages{
        stage("sonar quality check"){
            agent {
                docker {
                    image 'openjdk:11'
                }
            }
            steps{
                script{
                    withSonarQubeEnv(credentialsId: 'sonarQube') {
                            sh 'chmod +x gradlew'
                            //sh './gradlew sonarqube'
                            sh './gradlew sonar -Dsonar.projectKey=gradlebuild_app -Dsonar.host.url=http://34.125.99.18:9000 -Dsonar.login=sqp_ab25307f13a83a6371a64bb4758d41336d41ab33'
                    }
                }  
            }
        }
        
        
    }

}
