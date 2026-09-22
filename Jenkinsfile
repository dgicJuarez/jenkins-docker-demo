pipeline {
    agent any

    triggers {
        pollSCM('H/2 * * * *')
    }

    stages {
        stage('Información') {
            steps {
                echo 'Jenkins obtuvo el proyecto correctamente'
                sh 'git --version'
            }
        }

        stage('Ejecutar aplicación') {
            steps {
                sh 'sh app.sh'
            }
        }

        stage('Prueba') {
            steps {
                sh '''
                    resultado="$(sh app.sh)"
                    test "$resultado" = "Hola desde Jenkins"
                '''
            }
        }
    }

    post {
        success {
            echo 'Todas las pruebas terminaron correctamente'
        }

        failure {
            echo 'La prueba falló'
        }
    }
}