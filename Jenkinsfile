pipeline {
  agent any 
  // tools {
  //   maven 'Maven'
  // }
  stages {
    stage ('Initialize') {
      steps {
        sh '''
                echo "PATH = ${PATH}"
                echo "M2_HOME = ${M2_HOME}"
            ''' 
      }
     }
    
    stage ('Check secrets') {
      steps {
      sh 'trufflehog3 https://github.com/gaikwad-kunal/SSDLC.git -f json -o truffelhog_output.json || true'
      //sh './truffelhog_report.sh'
      }
    }
    
   stage ('Software composition analysis') {
            steps {
                dependencyCheck additionalArguments: ''' 
                    -o "./" 
                    -s "./"
                    -f "ALL" 
                    --prettyPrint''', odcInstallation: 'owasp-dc'

                dependencyCheckPublisher pattern: 'dependency-check-report.xml'
		   // sh './dependency_check_report.sh'
            }
        }
    
    
    stage ('SAST - SonarQube') {
      steps {
        withSonarQubeEnv('sonar') {
          sh 'mvn clean sonar:sonar -Dsonar.java.binaries=src'
	  //sh 'sudo python3 sonarqube.py'
	 // sh './sonarqube_report.sh'
        }
      }
    }
	  
    
    stage ('Generate build') {
      steps {
        sh 'mvn clean install -DskipTests'
      }
    } 
	  
   }  
}
