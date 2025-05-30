pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Clone the repo
                git branch: 'main', url: 'https://github.com/Only13harsh/My_Portfolio.git'
            }
        }
        stage('Lint HTML') {
            steps {
                // Optional: Install tidy if not already installed
                sh 'which tidy || sudo yum install -y tidy'
                // Lint all HTML files
                sh 'tidy -q -e *.html || true'
            }
        }
        stage('Deploy') {
            steps {
                // Clean old files (be careful with this)
                sh 'sudo rm -rf /var/www/html/*'
                // Copy all website files to Apache root
                sh 'sudo cp -r * /var/www/html/'
                // Set proper permissions
                sh 'sudo chown -R apache:apache /var/www/html/'
            }
        }
    }
}
