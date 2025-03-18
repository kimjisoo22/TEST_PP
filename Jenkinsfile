pipeline{
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git  crendtialsID : 'kimjisoo22',url: 'https://github.com/kimjisoo22/TEST_PP.git', branch='main'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat '''
                python -m venv venv
                call venu\\Script\\activate
                pip install --upgrade pip
                pip install -r requierment.txt
                '''
            }
        }

        stage('Run Tests') {
            steps {
                bat '''
                call venu\\Scripts\\activate
                pytest test_hello.py
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying Application...'

                bat '''
                    call venv\\Scripts\\activate
                    python hello_world.py
                    '''
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