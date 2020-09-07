pipeline {
    agent any
    stages {
        stage('Example Build') {
            steps {
                echo "monorepo"
                script{
                    def changeLogSets = currentBuild.rawBuild.changeSets
                    for (int i = 0; i < changeLogSets.size(); i++) {
                        def entries = changeLogSets[i].items
                        for (int j = 0; j < entries.length; j++) {
                            def entry = entries[j]
                            echo "${entry.commitId} by ${entry.author} on ${new Date(entry.timestamp)}: ${entry.msg}"
                            def files = new ArrayList(entry.affectedFiles)
                            for (int k = 0; k < files.size(); k++) {
                                def file = files[k]
                                echo "  ${file.editType.name} ${file.path}"
                            }
                        }
                    }
                }
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
