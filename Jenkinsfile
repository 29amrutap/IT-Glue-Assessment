pipeline {
    agent any
    parameters {
        string(name: 'host', description: 'Enter the host ip to update windows')
        string(name: 'user', description: 'Enter username to run connect to windows and run windows_updarte playbook')
        string(name: 'password', description: 'Enter password to connect to the windows host')
    }

    stages {
        stage('update') {
            steps {
                git branch: 'main', url: 'https://github.com/29amrutap/IT-Glue-Assessment.git'
                sh "ansible-playbook windows_update.yml -i hosts --extra-vars \"ansible_user=${params.user} ansible_password=${params.password}\" --limit ${params.host}"

            }

        }
    }
}
