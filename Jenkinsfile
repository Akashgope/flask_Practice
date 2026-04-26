pipeline {
    agent any

    environment {
        VENV_DIR = "${WORKSPACE}/venv"
    }

    stages {
        stage('Build') {
            steps {
                echo 'Installing dependencies...'
                sh '''
                    python3 -m venv $VENV_DIR
                    . $VENV_DIR/bin/activate
                    pip install --upgrade pip
                    pip install -r requirements.txt
                '''
            }
        }
        stage('Test') {
            steps {
                echo 'Running unit tests...'
                sh '''
                    . $VENV_DIR/bin/activate
                    pip install pytest
                    pytest test_app.py --maxfail=1 --disable-warnings || true
                '''
            }
        }
        stage('Deploy') {
            when {
                branch 'main'
            }
            steps {
                echo 'Deploying to staging environment...'
                sh '''
                    . $VENV_DIR/bin/activate
                    lsof -ti:5000 | xargs kill -9 || true
                    nohup python app.py --host=0.0.0.0 --port=5000 > staging.log 2>&1 &
                    echo "Flask app started on port 5000"
                '''
            }
        }
    }

    post {
        success {
            echo "Pipeline succeeded!"
        }
        failure {
            echo "Pipeline failed!"
        }
    }
}
