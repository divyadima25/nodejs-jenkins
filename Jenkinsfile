pipeline {
  agent any
    
  tools {nodejs "node"}
    
  stages {
        
    stage("Build") {
      steps {
        sh "sudo npm install"
        sh "sudo cd src"
        sh "sudo npm run build"
        sh "cp -R build /var/www/html/build"
        }
    }
  
  }
}
