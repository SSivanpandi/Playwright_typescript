pipeline {
    agent any
    stages {
        stage('Install playwright') {
            steps {
                sh '''
                npm i -D @playwright/test
                npx playwright install
                '''
            }
        }
          stage('help') {
            steps {
                sh 'npx playwright test --help'
            }
        }
        stage('Run Playwright Tests') {
            steps {
                sh '''
                npx playwright test --list
                npx playwright test
                '''
            }
        }
    }
}
