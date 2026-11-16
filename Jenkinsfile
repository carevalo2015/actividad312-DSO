pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo 'ETAPA 1: BUILD'
                echo 'Verificando el codigo fuente'

                sh 'python3 -m py_compile hola.py'
            }
        }

        stage('Test') {
            steps {
                echo 'ETAPA 2: TEST'
                echo 'Ejecutando pruebas unitarias'

                sh 'python3 -m unittest discover -v'
            }
        }

        stage('Deploy') {
            steps {
                echo 'ETAPA 3: DEPLOY'
                echo 'Desplegando aplicacion de prueba'

                sh '''
                    mkdir -p despliegue
                    cp hola.py despliegue/
                    python3 despliegue/hola.py
                '''
            }
        }
    }

    post {
        success {
            echo 'PIPELINE COMPLETADO CORRECTAMENTE'
        }

        failure {
            echo 'ERROR EN LA EJECUCION DEL PIPELINE'
        }
    }
}

