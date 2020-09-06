pipeline {
    agent any
    stages {
        stage('Example Build') {
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
