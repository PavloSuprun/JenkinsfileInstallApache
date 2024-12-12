def remote=[:]
remote.name = 'osboxes'
remote.host = '192.168.0.92'
remote.allowAnyHosts = true

pipeline {
    agent any

    environment {
        SSH_CREDENTIALS = credentials('remote-ssh-osboxes-credentials')
    }

    stages {
        stage('Install Apache2 on Remote Server') {
            steps {
                script {
                    remote.user = env.SSH_CREDENTIALS_USR
                    remote.password = env.SSH_CREDENTIALS_PSW
                }
                
                sshCommand(remote: remote, command: 'sudo apt update && sudo apt install -y apache2')
            }
        }
    }
}
