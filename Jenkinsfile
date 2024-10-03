pipeline {
    agent any

    // environment {
    //     NODEJS_HOME = tool name: 'NodeJS', type: 'NodeJSInstallation'
    //     PATH = "${NODEJS_HOME}/bin:${env.PATH}"
    // }

    tools {
        nodejs 'NodeJS'  // The name you configured for Node.js in Jenkins Global Tool Configuration
    }

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/Surya-2004/DevOps-Jenkins-Practice.git'
            }
        }
        
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                // Add your test command here, e.g., npm test
                echo 'Running Tests...'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the application...'
                sh 'npm run build' // If your project has a build step
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                sh 'scp -r ./ ubuntu@13.60.51.121: pm2 restart myapp || pm2 start /var/www/myapp/index.js --name myapp'
            }
        }
    }

    post {
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
