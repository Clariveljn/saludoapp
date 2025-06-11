pipeline {
    agent any

    tools {
        maven 'Maven 3.8.6'
        jdk 'JDK11'
    }

    stage('Clonar') {
        steps {
            git url: 'https://github.com/Clariveljn/saludoapp.git',
                branch: 'main',
                credentialsId: 'github-pat'
        }
    }

        stage('Compilar') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Probar') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Empaquetar') {
            steps {
                sh 'mvn package'
            }
        }
    }

    post {
        success {
            echo "🎉 El build fue exitoso"
        }
        failure {
            echo "💥 El build falló"
        }
    }
}