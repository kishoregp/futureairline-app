podTemplate(containers: [
    containerTemplate(
        name: 'test', image: 'maven:3-alpine',
        resourceRequestCpu: '50m', resourceLimitCpu: '500m',
        resourceRequestMemory: '200Mi', resourceLimitMemory: '500Mi',
        ttyEnabled: true, command: 'cat'),
  ], namespace: 'jenkins', 
) {

    node(POD_LABEL) {
        stage('Get maven project') {
            git url: 'https://github.com/jenkins-docs/simple-java-maven-app.git'
            container('test') {
                stage('Run an Maven build') {
                    sh """
                        mvn clean install
                    """
                }
                stage('Test') {
                    sh """
                        mvn clean install
                    """
                }
            }
        }
    }
}