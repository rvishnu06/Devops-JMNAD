pipeline{
    //Directives
    agent any
    tools {
        maven 'maven'
    }

    stages {
        // Specify various stage with in stages

        // stage 1. Build
        stage ('Build'){
            steps {
                sh 'mvn clean install package'
            }
        }

        // Stage2 : Testing
        stage ('Test'){
            steps {
                echo ' testing......'

            }
        }

        // Stage3 : Publish the artifacts to Nexus
        stage ('Publish artifacts to Nexus'){
            steps {
                nexusArtifactUploader artifacts: [[artifactId: 'VinayDevOpsLab', classifier: '', file: 'target/Vishnulab-0.0.1-SNAPSHOT.war',type: 'war']], credentialsId: 'b67bcd88-8cf1-456d-b883-6f0bfa004f68', groupId: 'com.vinaysdevopslab',nexusUrl: '172.20.10.253:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'VinayDevOpsLab-Snapshot', version: '0.0.1-SNAPSHOT'
                }
            }

    }

}
