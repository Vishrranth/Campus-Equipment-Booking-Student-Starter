stages {
    stage('Checkout and Inspect') {
        steps {
            sh 'echo "Building Campus Equipment Booking Service"'
            sh 'git branch --show-current'
            sh 'git log -1 --oneline'
        }
    }

    stage('Maven Test') {
        steps {
            sh 'mvn clean test'
        }
    }

    stage('Package Application') {
        steps {
            sh 'mvn clean package'
            sh 'ls -lh target/*.jar'
        }
    }

    stage('Build Docker Image') {
        steps {
            sh 'docker build -t campus-equipment-booking:set-b .'
        }
    }

    stage('Verify Docker Image') {
        steps {
            sh 'docker image inspect campus-equipment-booking:set-b'
        }
    }
}

post {
    success {
        echo 'CI pipeline completed successfully!'
    }

    failure {
        echo 'Pipeline failed. Check the stage logs.'
    }
}

