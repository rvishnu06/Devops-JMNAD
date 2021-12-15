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
              nexusArtifactUploader artifacts: [[artifactId: 'VinayDevOpslab', classifier: '', file: 'target/VinayDevOpslab-0.0.01.war', type: 'war']], credentialsId: 'd005804b-0f90-4357-8173-ecf3185a532e', groupId: 'com.vinaysdevopslab', nexusUrl: '172.20.10.16:8081', nexusVersion: 'nexus2', protocol: 'http', repository: 'VinayDevops-Release', version: '0.0.01'
            }
        }
    }
 }
