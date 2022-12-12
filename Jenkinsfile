pipeline{
    agent any
    tools{
        maven 'local_maven'
    }
    stages{
        stage ('Build'){
            steps{
                bat 'mvn clean package'
            }
            post{
                success{
                    echo "Archiving the Artifacts"
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage ('Deploy to tomcat server') {
            steps{
                echo "This is running"
                deploy adapters: [tomcat9(credentialsId: '2af4d53d-cef8-4a03-8921-1f1d61c9d607', path: '', url: 'http://localhost:8085/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}