pipeline{
    //Directives
    agent any
    tools {
        maven 'maven'
    }

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
                nexusArtifactUploader artifacts:
                [[artifactId: 'VinayDevOpslab',
                classifier: '',
                file: 'target/VinayDevOpslab-0.0.01.war',
                type: 'war']],
                credentialsId: 'b67bcd88-8cf1-456d-b883-6f0bfa004f68',
                groupId: 'com.vinaysdevopslab',
                nexusUrl: '172.20.10.253:8081',
                nexusVersion: 'nexus3',
                protocol: 'http',
                repository: 'VishnuDevops-lab-release',
                version: '0.0.01'
              }
        }
   }
