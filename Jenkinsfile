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
      
    
    stage ('Generate build') {
      steps {
        sh 'mvn clean install -DskipTests'
      }
    } 




  //  stage ('Deploy to server') {
  //           steps {
	 //  timeout(time: 3, unit: 'MINUTES') {
  //             sshagent(['app-server']) {
  //               sh "scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/'Secure Software Development Life Cycle (SSDLC)'/webgoat-server/target/webgoat-server-v8.2.0-SNAPSHOT.jar ubuntu@54.146.50.221:/WebGoat/"
		// sh 'ssh -o  StrictHostKeyChecking=no ubuntu@54.146.50.221 "nohup java -jar /WebGoat/webgoat-server-v8.2.0-SNAPSHOT.jar &"'
  //                 }
	 //     }
  //       }     
  //  }
   
  //   stage ('DAST - OWASP ZAP') {
  //           steps {
  //          sshagent(['dast-server']) {
  //               sh 'ssh -o  StrictHostKeyChecking=no ubuntu@3.231.68.129 "sudo docker run --rm -v /home/ubuntu:/zap/wrk/:rw -t owasp/zap2docker-stable zap-full-scan.py -t http://54.146.50.221:8080/WebGoat -x zap_report || true" '
		// //sh 'ssh -o  StrictHostKeyChecking=no ubuntu@3.231.68.129 "./zap_report.sh"'
  //             }      
  //          }       
    // }
	  
   }  
}
