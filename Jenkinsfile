pipeline {
    agent any

    environment {
        IMAGE_NAME = 'proyectofinal'
        IMAGE_NAME_TEST = 'proyectofinaltesting'
        DOCKER_USARNAME = 'Gabriizdr'
        DCOKER_CREDENTIAL = 'docker-hub-creds'
        DOCKER_IMAGE = "${DOCKER_USARNAME}/${IMAGE_NAME}"
    }

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
                    docker.build(IMAGE_NAME_TEST, "--file=Dockerfile.test .")
                }
            }
        }

        stage ('Build') {
            steps {
                docker.build(DOCKER_IMAGE, ".")
            }
        }
    }
}
