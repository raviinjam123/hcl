node
{
     def mavenHome = tool name: "maven3.6.2"
    
    stage('Code Checkout')
    {
        git credentialsId: '756d09a6-141a-483c-bbfb-f83ca5592da1', url: 'https://github.com/raviinjam/hcl.git'
    }
    
    stage('build')
    {
        sh "${mavenHome}/bin/mvn clean package"
        
    }
    
     stage('ExecuteSonarQubeReport')
    {
     sh "${mavenHome}/bin/mvn sonar:sonar"

    }
    
    stage('DeployAppIntoTomcatServer')
    {
     deploy adapters: [tomcat9(credentialsId: 'c8f280b8-127d-400a-9063-c1b2e8156c12', path: '', url: 'http://13.233.194.19:8080/')], contextPath: null, war: '**/*.war'
    }
}
