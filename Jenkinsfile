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

        // Stage 3: Push to Nexus
        stage ('Deploy to Nexus') {
            steps {
              nexusArtifactUploader artifacts: [[artifactId: 'VinayDevOpslab', classifier: '', file: 'target/VinayDevOpslab-0.0.01', type: 'war']], credentialsId: 'd005804b-0f90-4357-8173-ecf3185a532e', groupId: 'com.vinaysdevopslab', nexusUrl: '13.58.170.220:8081', nexusVersion: 'nexus2', protocol: 'http', repository: 'Devops-Release', version: '0.0.01'
            }
        }
    }
 }
