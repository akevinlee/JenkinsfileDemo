pipeline {
    agent any
	
	parameters {
		booleanParam(name: 'DEPLOY_APP',
			defaultValue: params.DEPLOY_APP ?: false,
            description: 'Deploy the application')
	}

	environment {
		WEB_SERVER_URL = "${params.WEB_SERVER_URL_DEFAULT ?: 'http://my.webserver.com'}"
		GIT_URL = scm.getUserRemoteConfigs()[0].getUrl()    // Git Repo
	}	

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven 'M3'
    }
	
	stages {
        stage('Build') {
			agent any
			steps {
				
				script {
				
				    // Get code from Git repository 
                	//git url: "${env.GIT_URL}"
					
					println "DEPLOY_APP=${params.DEPLOY_APP}"
					println "WEB_SERVER_URL=${env.WEB_SERVER_URL}"
					// Print out our configurable parameters
					if (isUnix()) {
						sh "echo DEPLOY_APP=${params.DEPLOY_APP}"
                        sh "echo WEB_SERVER_URL=${env.WEB_SERVER_URL}"
						sh "mvn clean package"
                    } else {
						bat "echo DEPLOY_APP=${env.DEPLOY_APP}"
                        bat "echo WEB_SERVER_URL=${env.WEB_SERVER_URL}"
						bat "mvn clean package"
                    }
				}
				
			}
		}
	}	
}	