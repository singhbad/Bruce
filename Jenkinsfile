pipeline {
    agent {
        label "master"
    }
    tools {
        maven 'Maven3.1.1'
        jdk 'java8'
    }
	
	withEnv(['env.PATH = "${tool \'maven-3.3.9\'}/bin:${env.PATH}"', 
	'version = \'1.0.\' + env.BUILD_NUMBER', 
	'currentBuild.displayName = version']) {
    
	}
    stages 
	{
	stage ('Initialize') {
            steps {
                bat '''
                    echo "PATH = %PATH%"
                    echo "M2_HOME = %M2_HOME%"
                '''
            }
        }
		
		

        stage ('Build') {
            steps {
                    bat 'cd NumberGenerator & mvn -B -V -U -e clean package'
            }
             post {
                success {
                    junit 'NumberGenerator/target/surefire-reports/*.xml, allowEmptyResults: true'
                        }
                 }
               

           
            }
        }
    
}
