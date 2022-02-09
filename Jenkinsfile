podTemplate(containers: [containerTemplate(name: 'maven', image: 'maven', command: 'sleep', args: 'infinity')]) {
  node(POD_LABEL) {
    checkout scm
    environment {
     http_proxy='http://proxy-dmz.corpnet.inside:8080' 
     https_proxy='http://proxy-dmz.corpnet.inside:8080' 
     HTTP_PROXY='http://proxy-dmz.corpnet.inside:8080' 
     HTTPS_PROXY='http://proxy-dmz.corpnet.inside:8080'  
     
    }
    container('maven') {
      sh 'mvn -B -ntp -Dmaven.test.failure.ignore verify'
      sh 'env | sort'
    }
    junit '**/target/surefire-reports/TEST-*.xml'
  }
}
