pipeline {
    agent {label "zerosrv"}
    options {
        // Timeout counter starts AFTER agent is allocated
        timeout(time: 1, unit: 'MINUTES')
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                sh 'podman build -t zero-site-2:latest .'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                sh 'podman-compose down'
                sh 'podman-compose up -d'
            }
        }
    }
}
