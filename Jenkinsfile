pipeline {
  agent any
    
  tools {nodejs "node"}
    
  stages {
        
    stage("Build") {
      steps {
        sh "sudo npm install"
        sh "sudo npm run build"
        
        }
    }
    
    stage("Deploy") {
      steps {
        sh "scp -r build root@172.31.35.67:/usr/share/nginx/html/"
        sh 'ssh root@172.31.35.67 "systemctl restart nginx"'
        
      }
    }
  }
}
