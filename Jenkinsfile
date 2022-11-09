pipeline {
agent any
    stages {
        

        stage ("Git checkout "){
            steps{
        git branch: 'wagine', 
            url: 'https://github.com/alimejrii/devprj.git'
            }
        
        }
         stage("Quality code Test") {
            steps {
           
             sh 'mvn sonar:sonar -Dsonar.projectKey=a -Dsonar.host.url=http://192.168.58.64:9000 -Dsonar.login=cc0beb81a24d020b99dcced6805abaa50333ade7'         
                 
               

            }
         
    }}
