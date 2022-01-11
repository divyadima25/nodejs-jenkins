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
        sh "scp -o UserKnownHostsFile=/dev/null -o StrictHostKeyChecking=no -r build root@172.31.35.67:/usr/share/nginx/html/"
        sh 'ssh -o UserKnownHostsFile=/dev/null -o StrictHostKeyChecking=no root@172.31.35.67 "systemctl restart nginx"'
        
      }
    }
  }
}
