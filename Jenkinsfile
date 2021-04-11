node('master') {
  
  
    stage('git') {
    
     git credentialsId: 'jenkinsgit', url: 'git@gitlab.com:khlifidev1/projet_j2e.git'
     
    }
  
    stage('Maven'){
        sh 'mvn clean install package'
    }
  
    stage('deploy_tomcat'){
        deploy adapters: [tomcat8(credentialsId: 'user_tomcat', path: '', url: 'http://172.16.254.21:8080/webapp/')], contextPath: null, war: '**/*.war'
    }
  
  
}
