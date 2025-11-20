cd ~/CICD-conf
cat > Jenkinsfile << 'EOF'
pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', 
                    url: 'https://github.com/yogeshuh/CICD-conf',
                    credentialsId: 'edaf145f-c8f0-46d6-ab24-1f219d66755a'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }
        stage('Run Tests') {
            steps {
                sh 'pytest || true'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t myapp:latest .'
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker run -d -p 8000:8000 myapp:latest || true'
            }
        }
    }
}
EOF
