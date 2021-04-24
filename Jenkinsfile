node { 
    
    def mvnHome = tool (name: 'maven', type: 'maven')


    stage('clone') {
        
    git 'https://gitlab.com/khlifidev1/projet_j2e.git'
    
    }
    
    stage('build') {
    
    sh "'${mvnHome}/bin/mvn' clean install"
    
    }

    stage('build_img'){

      sshPublisher(publishers: [sshPublisherDesc(configName: 'ansible_server', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: '', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '//opt//docker', remoteDirectorySDF: false, removePrefix: '**/*', sourceFiles: '**/*.war')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])

        sshPublisher(publishers: [sshPublisherDesc(configName: 'ansible_server', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: 'docker build -t myapp /opt/docker ', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '//opt//docker', remoteDirectorySDF: false, removePrefix: '', sourceFiles: 'Dockerfile')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
    }







    

}
