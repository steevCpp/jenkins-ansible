node { 
    
    stage('clone') {
        
    git 'https://gitlab.com/khlifidev1/projet_j2e.git'
    
    }
    
    stage('build') {
    
    sh'mvn clean install package'
    
    }
    
    stage('deploy') {
    
     //sh "ansible-playbook copy.yml" 
     //ansiblePlaybook 'copy.yml'
     //ansiblePlaybook become: true, becomeUser: 'ansadmin', colorized: true, credentialsId: 'ansjenkins', inventory: 'hosts.yml', playbook: 'copy.yml'

     sshPublisher(publishers: [sshPublisherDesc(configName: 'ansible_server', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: 'ansible-playbook -i hosts.yml copy.yml', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '/opt/ansible', remoteDirectorySDF: false, removePrefix: '', sourceFiles: 'copy.yml, hosts.yml')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
    }
    
    
}
