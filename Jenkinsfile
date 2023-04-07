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
                    withSonarQubeEnv(credentialsId: 'sonarqube-mss-warmart-prod-jenkins-pipeline-connection', installationName: 'sonarQube') {
                            sh 'chmod +x gradlew'
                            sh './gradlew clean build -d sonarqube'
                    }
                }  
            }
        }
        
        
    }

}
