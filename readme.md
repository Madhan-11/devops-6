tools {
    maven 'Maven'
    jdk 'JDK'
}

stages {

    stage('Checkout') {
        steps {
            git branch: 'main', url: 'https://github.com/swastisudha2025-source/devops_project.git'

        }
    }

    stage('Build') {
        steps {
            bat 'mvn clean package'
        }
    }

    stage('Test') {
        steps {
            bat 'mvn test'
        }
    }
}
post {
    always {
                junit allowEmptyResults: true, testResults: '**/target/surefire-reports/*.xml'

    }
}
