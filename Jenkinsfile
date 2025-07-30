pipeline {
    agent any

    triggers {
        githubPush()
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Gabriizdr/proyectofinal.git'
            }
        }

        stage('Test') {
            steps {
                script {
                    docker.build("proyectofinaltesting", "--file=Dockerfile.test .")
                }
            }
        }
    }
}
