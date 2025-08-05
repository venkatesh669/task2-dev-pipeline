pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'venkatesh86/myapp'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/venkatesh669/your-repo.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the app...'
                sh 'docker build -t $DOCKER_IMAGE .'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                // Add actual test commands here
                sh 'echo "No tests defined yet"'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Pushing image to DockerHub...'
                withCredentials([usernamePassword(credentialsId: '10a0992a-1033-4923-937a-124b0c93b4fe', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                    sh 'echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin'
                    sh 'docker push $DOCKER_IMAGE'
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}

