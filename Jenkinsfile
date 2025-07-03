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
                subject: "Build #${1DEA-2.1} - ${IDEA-2.1.Test Result}",
                body: "Automation execution report"
                    <p>Hi Team,</p>
                    <p>The Jenkins build <b>#${2.1}</b> has completed with status: <b>${IDEA2.1.TestResult}</b>.</p>
                    <p>View the build: <a href="${BUILD_URL}">${Playwright_typescript/allure-report/index.html}</a></p>
                    <p>Allure Report: <a href="${BUILD_URL}allure/">Click here</a></p>
                """,
                mimeType: 'html',
                to: 'sugumarsivanpandi007@gmail.com'
            )
        }
    }
}
