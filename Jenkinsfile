pipeline {
    agent {
	    label 'slave1'
      stages {
        stage('checkout') {
	   
            steps {
		sh 'rm -rf hello-world-war'    
		sh 'git clone https://github.com/prabhakanth/hello-world-war/'
            }
        }
	stage('Build') {
            steps {		
		sh 'mvn clean package'
	    }
	}stage('tomcat installation') {
            steps {		
		sh 'sh tomcat.sh'
	    }
	}
	      
        stage('deploy') {
	     agent {
	     label 'slave2'
            }
            steps {
		    echo "good "
	            sh 'sudo cp /home/ubuntu/workspace/tom_installation/target/hello-world-war-3.0.0.war /var/lib/tomcat9/webapps'//
            }
        }    
    }
}
