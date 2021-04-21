node { 
    
    def mvnHome = tool (name: 'maven', type: 'maven')


    stage('clone') {
        
    git 'https://gitlab.com/khlifidev1/projet_j2e.git'
    
    }
    
    stage('build') {
    
    sh "'${mvnHome}/bin/mvn' clean install"
    
    }
    
    stage('deploy') {
    
     //sh "ansible-playbook copy.yml" 
     //ansiblePlaybook 'copy.yml'
     //ansiblePlaybook become: true, becomeUser: 'ansadmin', colorized: true, credentialsId: 'ansjenkins', inventory: 'hosts.yml', playbook: 'copy.yml'

sshPublisher(publishers: [sshPublisherDesc(configName: 'ansible_server', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: 'ansible-playbook -i  /opt/ansible/hosts.yml    /opt/ansible/copy.yml', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '//opt//ansible', remoteDirectorySDF: false, removePrefix: 'webapp/target/', sourceFiles: 'webapp/target/webapp.war, copy.yml, hosts.yml')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
  
    }
    
}
