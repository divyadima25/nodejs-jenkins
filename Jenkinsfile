pipeline {
  agent any
    
  tools {nodejs "node"}
    
  stages {
        
    stage("Build") {
		if (env.BRANCH_NAME == 'master' && env.BRANCH_NAME == 'dev' ) {
			steps {
				sh "sudo npm install"
				sh "sudo npm run build"
			}  
        }
    }
    
	stage("Deploy to DEV") {
		if (env.BRANCH_NAME == 'dev' ) {
			steps {
				sh "scp -o UserKnownHostsFile=/dev/null -o StrictHostKeyChecking=no -r build root@172.31.35.67:/usr/share/nginx/html/"
				sh 'ssh -o UserKnownHostsFile=/dev/null -o StrictHostKeyChecking=no root@172.31.35.67 "systemctl restart nginx"'
			}
		}
    }
	
	stage("Deploy to Production") {
		if (env.BRANCH_NAME == 'master' ) {
			steps {
				sh "scp -o UserKnownHostsFile=/dev/null -o StrictHostKeyChecking=no -r build root@172.31.35.67:/usr/share/nginx/html/"
				sh 'ssh -o UserKnownHostsFile=/dev/null -o StrictHostKeyChecking=no root@172.31.35.67 "systemctl restart nginx"'
			}
		}
    }

  }
}
