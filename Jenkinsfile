node {
   stage('Preparation') {
      // Get some code from a GitHub repository
      git branch: 'dev', url: 'https://github.com/ciber96/WordPress'
      stash 'repo'
   }
   stage('Build') {
      sh label: '', script: 'zip -r data.zip .'
      stash 'repo'
   }
   stage('Deploy') {
       sshPublisher(publishers: [sshPublisherDesc(configName: 'Wordpress Prod', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: 'unzip -o /home/vagrant/wp-content/data.zip', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '', remoteDirectorySDF: false, removePrefix: '', sourceFiles: 'data.zip')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
   }
}