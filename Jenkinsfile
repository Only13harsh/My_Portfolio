pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Only13harsh/My_Portfolio.git'
            }
        }
        // Commented out Lint HTML stage because tidy is not available
        /*
        stage('Lint HTML') {
            steps {
                sh 'tidy -q -e *.html || true'
            }
        }
        */
        stage('Deploy') {
            steps {
                sh '''
                  sudo rm -rf /var/www/html/*
                  sudo cp -r * /var/www/html/
                  sudo chown -R apache:apache /var/www/html/
                '''
            }
        }
    }
}
