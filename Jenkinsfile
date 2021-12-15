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
            nexusArtifactUploader artifacts: [[artifactId: 'VinayDevOpslab', classifier: '', file: 'target/VinayDevOpslab-0.0.02.war', type: 'war']], credentialsId: 'd005804b-0f90-4357-8173-ecf3185a532e', groupId: 'com.vinaysdevopslab', nexusUrl: '13.58.170.220:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'VinayDevops-Release', version: '0.0.02'
            }
        }

        // stage 4: Deploy to tomcat
        stage ('Deploy to tomcat'){
            steps {
              sshPublisher(publishers: [sshPublisherDesc(
                configName: 'Ansible_Controller',
                transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: 'ansible-playbook /opt/playbooks/downloaddeploy.yml -i /opt/playbooks/hosts', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '', remoteDirectorySDF: false, removePrefix: '', sourceFiles: '')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
            }
        }


    }
}
