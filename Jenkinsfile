podTemplate(containers: [containerTemplate(name: 'maven', image: 'maven', command: 'sleep', args: 'infinity')]) {
  node(POD_LABEL) {
    checkout scm
   
    withEnv([ http_proxy='http://proxy-dmz.corpnet.inside:8080',https_proxy='http://proxy-dmz.corpnet.inside:8080',HTTP_PROXY='http://proxy-dmz.corpnet.inside:8080',HTTPS_PROXY='http://proxy-dmz.corpnet.inside:8080']) {
    container('maven') {
      
      sh 'env | sort'
      sh 'mvn -B -ntp -Dmaven.test.failure.ignore verify'
      }
    }
    junit '**/target/surefire-reports/TEST-*.xml'
  }
}
