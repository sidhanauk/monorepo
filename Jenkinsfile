pipeline {
    agent any
    stages {
        stage('Example Build: feature2') {
            steps {
                echo "monorepo"
            }
        }
        stage('Trigger Helm Charts'){
            steps{
                script{
                    build job: "../Helm-Charts/helm1/${BRANCH_NAME}"
                }
            }
        }
    }
}
