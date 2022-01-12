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
        sh "scp -o UserKnownHostsFile=/dev/null -o StrictHostKeyChecking=no -r build root@13.233.237.11:/usr/share/nginx/html/"
        sh 'ssh -o UserKnownHostsFile=/dev/null -o StrictHostKeyChecking=no root@13.233.237.11 "systemctl restart nginx"'
        
      }
    }
  }
}
