pipeline{
    agent{ label "OI_GradleBuild_App"}
    environment{
        VERSION = "${env.BUILD_ID}"
        sonarToken = credentials('sonarQube')
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
                    withSonarQubeEnv(credentialsId: 'sonarToken') {
                            sh 'chmod +x gradlew'
                            sh './gradlew sonarqube'
                    }
                }  
            }
        }
        
        
    }

}
