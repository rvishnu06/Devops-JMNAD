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
        stage ('Publish to Nexus'){
            steps {
            nexusArtifactUploader artifacts: [[artifactId: 'Vishnulab', classifier: '', file: 'target/Vishnulab-0.0.1-SNAPSHOT.war',
type: 'war']], credentialsId: 'b67bcd88-8cf1-456d-b883-6f0bfa004f68', groupId: 'com.vinaysdevopslab',
nexusUrl: '172.20.10.253:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'VishnuDevopsLab-Snapshot',
version: '0.0.1-SNAPSHOT'
            }
        }
/*
        // Stage 4 : Print some information
        stage ('Print Environment variables'){
                    steps {
                        echo "Artifact ID is '${ArtifactId}'"
                        echo "Version is '${Version}'"
                        echo "GroupID is '${GroupId}'"
                        echo "Name is '${Name}'"
                    }
                }

        // Stage 5 : Deploying the build artifact to Apache Tomcat
        stage ('Deploy to Tomcat'){
            steps {
                echo "Deploying ...."
                sshPublisher(publishers:
                [sshPublisherDesc(
                    configName: 'Ansible_Controller',
                    transfers: [
                        sshTransfer(
                                cleanRemote:false,
                                execCommand: 'ansible-playbook /opt/playbooks/downloadanddeploy_as_tomcat_user.yaml -i /opt/playbooks/hosts',
                                execTimeout: 120000
                        )
                    ],
                    usePromotionTimestamp: false,
                    useWorkspaceInPromotion: false,
                    verbose: false)
                    ])

            }
        }

    // Stage 6 : Deploying the build artifact to Docker
        stage ('Deploy to Docker'){
            steps {
                echo "Deploying ...."
                sshPublisher(publishers:
                [sshPublisherDesc(
                    configName: 'Ansible_Controller',
                    transfers: [
                        sshTransfer(
                                cleanRemote:false,
                                execCommand: 'ansible-playbook /opt/playbooks/downloadanddeploy_docker.yaml -i /opt/playbooks/hosts',
                                execTimeout: 120000
                        )
                    ],
                    usePromotionTimestamp: false,
                    useWorkspaceInPromotion: false,
                    verbose: false)
                    ])

            }
        }

*/
}
