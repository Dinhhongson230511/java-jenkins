pipeline {
    agent any
    tools {
        maven "MAVEN3"
        jdk "OracleJDK17"
    }

    environment {
        SNAP_REPO = 'project-snapshots'
        NEXUS_USER = 'admin'
        NEXUS_PASS = 'dHS|sondh3@Rikkeisoft|dHS'
        RELEASE_REPO = 'project-release-artifacts'
        CENTRAL_REPO = 'project-maven-central'
        NEXUS_IP = '172.31.39.124'
        NEXUS_PORT = '8081'
        NEXUS_GRP_REPO = 'project-maven-group'
        NEXUS_LOGIN = 'nexuslogin'
    }

    stages {
        stage('Build'){
            steps {
                sh 'mvn -s settings.xml -DskipTests install'
            }
            post {
                success {
                    echo 'Archiving'
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
            
        }

	    stage('UNIT TEST'){
            steps {
                sh 'mvn test'
            }
        }

	    stage('INTEGRATION TEST'){
            steps {
                sh 'mvn verify -DskipUnitTests'
            }
        }
		
        stage ('CODE ANALYSIS WITH CHECKSTYLE'){
            steps {
                sh 'mvn checkstyle:checkstyle'
            }
            post {
                success {
                    echo 'Generated Analysis Result'
                }
            }
        }
    }    
}