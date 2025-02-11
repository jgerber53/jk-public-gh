pipeline {
    agent any

    stages {
        stage('Cloning Git Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/jgerber53/jk-public-gh.git'
            }
        }
        
        stage('Building Image') {
            steps {
                sh 'docker build -t webapp:${BUILD_NUMBER} .'
            }
        }
        
        stage('Deploying Application') {
            steps {
                sh '''
                # comment the next line if you have no container running.
                # docker stop webapp_ctr
                docker run --rm -d -p 3000:3000 --name webapp_ctr webapp:${BUILD_NUMBER}
            '''
            }
        }
    }
}
