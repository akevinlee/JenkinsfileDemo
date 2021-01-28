pipeline {
    agent any
	
	parameters {
		booleanParam(name: 'DEPLOY_APP',
			defaultValue: params.DEPLOY_APP_DEFAULT ?: false,
            description: 'Deploy the application')
	}

	environment {
		WEB_SERVER_URL = ${params.WEB_SERVER_URL_DEFAULT ?: "http://my.webserver.com"}
	}	
		
	stages {
        stage('Build') {
			agent { any }
			steps {
				
				script {
					if (isUnix()) {
						sh "echo DEPLOY_APP=${params.DEPLOY_APP}"
                        sh "echo WEB_SERVER_URL=${env.WEB_SERVER_URL}"
                    } else {
						bat "echo DEPLOY_APP=${env.DEPLOY_APP}"
                        bat "echo WEB_SERVER_URL=${env.WEB_SERVER_URL}"
                    }
				}
				
			}
		}
	}	
}	