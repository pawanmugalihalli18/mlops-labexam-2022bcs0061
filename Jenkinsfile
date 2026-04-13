pipeline {
    agent any

    stages {

        stage('Install Dependencies') {
            steps {
                sh '''
                python3.11 -m venv venv
                . venv/bin/activate
                pip install --upgrade pip
                pip install pandas scikit-learn joblib
                '''
            }
        }

        stage('Train Model') {
            steps {
                sh '''
                . venv/bin/activate
                python scripts/train.py
                '''
            }
        }

        stage('Print Metrics') {
            steps {
                sh '''
                echo "===== MODEL METRICS ====="
                cat metrics.json
                echo "Name: Mugalihalli Pawan"
                echo "Roll No: 2022BCS0061"
                '''
            }
        }

        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: 'model.pkl, metrics.json', fingerprint: true
            }
        }
    }
}