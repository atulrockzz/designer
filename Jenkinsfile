pipeline {
   agent any
	stages {
      stage('SCM Checkout') {
         steps {
            git 'https://github.com/atulrockzz/designer.git'
		}
	}
	stage('Build') {
		steps {
			sh '''
			npm install
			polymer build                       
			'''
		}
	}
	stage ('Deploy') {
		steps {
			sh '''
             cp -r $WORKSPACE/dist/designer /opt/apache-tomcat-9.0.30/webapps
             curl -u admin:admin http://18.219.117.106:8888/manager/reload?path=/build 
             '''
		}
	}
}
}
