pipeline {
    agent { 
        label 'JDK_8' 
    }

    options {
        timeout(time: 1, unit: 'HOURS')
    }

    triggers {  
        pollSCM('* * * * *')
    }


    stages {
        stage ( 'scorce code management' ) {
            steps {
                script { 
              git url: 'https://github.com/ippiliRajesh/game-of-life.git',
                  branch: 'master' 
            }
         }
        }
          
        stage ( 'build and package' ) {
            steps {
                sh 'mvn package'
            }
         }

        stage ( 'reports') {
            steps {
                junit testResults: 'gameoflife-web/target/surefire-reports/TEST-*.xml'
                archiveArtifacts artifacts: 'gameoflife-web/target/gameoflife.war'
                
            }
        }  
   }

 }