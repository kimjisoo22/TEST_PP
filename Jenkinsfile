pipeline{
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                     git credentialsId : 'pathelloworld' ,url: 'https://github.com/kimjisoo22/TEST_PP.git', branch : 'main'
            }
        }

        stage('Install Dependencies') {
            steps{
                bat '''
                python -m venv venv
                call venv\\Scripts\\activate
                pip install --upgrade pip
                pip install -r requirement.txt
                '''
            }
        }

        stage('Run Tests') {
            steps {
                bat '''
                call venv\\Scripts\\activate
                pytest test.py
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying Application...'

                bat '''
                    call venv\\Scripts\\activate
                    python hlo.py
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