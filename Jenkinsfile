pipeline {

    agent any

    stages {

        stage ('Build') {
            steps {
               
                    cmd 'mvn clean install -X'
              
            }
        }

        stage ('Deploy') {
            steps {

                withCredentials([[$class          : 'UsernamePasswordMultiBinding',
                                  credentialsId   : 'PCF_LOGIN',
                                  usernameVariable: 'USERNAME',
                                  passwordVariable: 'PASSWORD']]) {

                    cmd 'cf login -a http://api.run.pivotal.io -u $USERNAME -p $PASSWORD'
                    cmd 'cf push'
                }
            }

        }

    }

}
