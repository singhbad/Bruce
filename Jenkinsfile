node {
stage('Configure')
{
  env.PATH = "${tool 'maven-3.3.9'}/bin:${env.PATH}"
	version = '1.0.' + env.BUILD_NUMBER
	currentBuild.displayName = version
}


}
	
	
   
	
	
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
