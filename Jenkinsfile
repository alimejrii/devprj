pipeline {
agent any
    stages {
        

        stage ("Git checkout "){
            steps{
        git branch: 'wagine', 
            url: 'https://github.com/alimejrii/devprj.git'
            }
        
        }
             stage("Compile Project") {
            steps {
                echo "Compile Project"
                sh 'mvn compile -DskipTests=true'
            }
        }
       
        stage('Unit test') {
            steps {
                sh 'mvn test '
            }
        }
         
        
        stage("Build Project") {
            steps {
                echo "Build & test Project"
                sh 'mvn clean package -DskipTests=true'
            }
        }
         stage("Quality code Test") {
            steps {
           
             sh 'mvn sonar:sonar -Dsonar.projectKey=a -Dsonar.host.url=http://192.168.58.64:9000 -Dsonar.login=cc0beb81a24d020b99dcced6805abaa50333ade7'         
                 
               

            }
         }
        stage("Publish to Nexus Repository Manager") {
            steps {
                nexusPublisher nexusInstanceId: 'nexus',
                     nexusRepositoryId: 'nexus-repo', 
                     packages: [[$class: 'MavenPackage',
                                 mavenAssetList: [[classifier: '', 
                                                   extension: '', 
                                                   filePath: '/var/lib/jenkins/workspace/wijou/target/tpAchatProject-1.0.jar']], 
                                 mavenCoordinate: [artifactId: 'spring-boot-starter-parent', 
                                                   groupId: 'org.springframework.boot', 
                                                   packaging: 'jar', 
                                                   version: '2.5.3']]]

}
           }
       
    }}
