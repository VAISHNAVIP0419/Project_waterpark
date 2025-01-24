pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: '<git@github.com:VAISHNAVIP0419/Project_waterpark.git>'
            }
        }
        stage('Deploy to EC2') {
            steps {
                sshPublisher(
                    publishers: [
                        sshPublisherDesc(
                            configName: 'EC2-Server',
                            transfers: [
                                sshTransfer(
                                    sourceFiles: 'index.html',
                                    remoteDirectory: '/var/www/html',
                                    removePrefix: '',
                                    execCommand: 'sudo systemctl restart nginx'
                                )
                            ]
                        )
                    ]
                )
            }
        }
    }
}

