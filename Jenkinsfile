pipeline {
    agent any
    options {
                buildDiscarder logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '', numToKeepStr: '2')
                timestamps()
            }

    stages {
        stage('Test') {
            steps {
                git credentialsId: 'Github', url: 'https://github.com/PriyankaSharma0925/api-testing-postman'
                bat 'dir '
                bat '''echo "Code downloaded from Git"

newman run "TestingWorld.postman_collection.json" -e "%Environment%_Env.postman_environment.json"  -r htmlextra,allure --reporter-htmlextra-export results\\report.html  --suppress-exit-code'''

                
            }
        }
    }
}
