node { 
 
 stage('clone') {
    
    git 'https://gitlab.com/khlifidev1/projet_j2e.git'

 }
 
  stage('Build') {
    
      sh 'mvn clean install package'

 }
 
 stage('Deploy') {
    
     ansiblePlaybook become: true, inventory: 'hosts', playbook: 'copy.yml'

 }
 
    
}
