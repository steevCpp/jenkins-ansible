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
     ansiblePlaybook become: true, becomeUser: 'ansadmin', colorized: true, credentialsId: 'ansjenkins', inventory: 'hosts.yml', playbook: 'copy.yml'
    }
    
    
}
