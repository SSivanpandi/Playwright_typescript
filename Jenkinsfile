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
                npx playwright test

                '''
            }
        }
        stage('Generate Allure Report') {
            steps {
                sh 'allure generate allure-results -o allure-report --clean'
                }
        }
    }
    post {
            always {
                allure([
                    includeProperties: false,
                    jdk: '',
                    results: [[path: 'Playwright_typescript/allure-results']]
            ])
             emailext(
                subject: "Build #${BUILD_NUMBER} - ${currentBuild.currentResult}",
                body: "Build completed. Check details at: ${BUILD_URL}/Playwright_typescript/allure-report/index.html",
                mimeType: 'html',
                to: "sugumarsivanpandi007@gmail.com"
            )
        }
    }
}
