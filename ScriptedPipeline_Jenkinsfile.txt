node {
    stage('Cont Download from SCM')   {
    git 'https://github.com/venkat9822891/maven-project1.git'
                                      }
    stage('Cont Build using Maven tool') {
    sh 'mvn package'
                                         } 
    stage('Cont Deployment into dev environment') {
	deploy adapters: [tomcat9(credentialsId: '376b2036-53ce-4579-853b-aefec20188d1', path: '', url: 'http://172.31.13.36:8080')], contextPath: '/scr-app', war: '**/*.war'
	                                            }



}
