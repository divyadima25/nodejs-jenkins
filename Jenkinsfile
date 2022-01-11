pipeline {
  agent any
    
  tools {nodejs "node"}
    
  stages {
        
    stage("Build") {
      steps {
        sh "sudo npm install"
        sh "sudo npm run build"
        sh "sudo cp -R build /var/www/html/build"
        }
    }
  
  }
}
