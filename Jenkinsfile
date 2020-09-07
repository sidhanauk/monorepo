pipeline {
    agent any
    stages {
        stage('Example Build') {
            steps {
                echo "monorepo with feature2++ new feat"
            }
        }
        stage('Deploy Helm Charts'){
          when {
            branch 'master'
          }
          steps{
            script{
                build job: "../Helm-Charts/helm1/${BRANCH_NAME}"
                build job: "../Helm-Charts/helm2/${BRANCH_NAME}"
            }
          }
      }
   }
}
