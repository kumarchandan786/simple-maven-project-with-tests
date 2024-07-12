node {
    checkout scm

    stage('Build') {
        withMaven(maven: 'M3') {
            if (isUnix()) {
                sh 'mvn clean package'
            } else {
                bat 'mvn clean package'
            }
        }
    }

    stage('Results') {
        junit '**/target/surefire-reports/TEST-*.xml'
        archiveArtifacts artifacts: 'target/*.jar', allowEmptyArchive: true
    }
}

