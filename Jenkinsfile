pipeline {

  agent any

     stages {

        stage('pytest') {

           steps {

              script {

                 sh 'conftest.py'
                 sh'test_vector.py'
             }
           }
        }

        stage('SonarQube Analysis') {

           steps {

              script {

                 withSonarQubeEnv('Sonarqube') {

                    sh '''

                    /opt/sonar-scanner/bin/sonar-scanner \

                    -Dsonar.projectKey=Calculate \

                    -Dsonar.host.url=http://172.19.0.3:9000 \

                    -Dsonar.login=$SONARQUBE_CRED_USR -Dsonar.password=$SONARQUBE_CRED_PSW

                    '''

                }

              }

          }

        }





     }

  }

}
