pipeline {
    agent { lable 'JDK-17'}

    triggers {
        poolSCM('* * * * *')
    }

    tools {
        jdk 'JDK_17'
    }
    stages {
        stage ('vcs') {
           steps { 
              git url: 'https://github.com/Praneethysp007/jenkins.git',
                  branch: 'main'
           }
        }
    }    
        stage ('Build and package') {
           steps {
              sh script: 'mvn package'
           }
        }

        stage ('artifacts and testresult') {
            steps {
               archiveArtifacts artifacts: '**/target/*.jar'
               junit testResults: '**/target/surefire-reports/*.xml'
            }
        }   
}