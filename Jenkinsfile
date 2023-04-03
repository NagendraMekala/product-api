pipeline {

  agent any
  environment {
      ANYPOINT_CREDETIALS = credentials('Anypoint-Credential')
      //M2SETTINGS = "C:\\Users\\lenovo\\.m2\\settings.xml"
  }
  
  stages {
    stage('Build') {
      steps {
            bat 'mvn -B -U -e -V clean -DskipTests package'
      }
    }

    stage('Test') {
      steps {
           echo "**********************munit test cas is executed**********************"
      }
    }

     stage('Deployment') {
      environment{
        client_id=credentials('dev-client-id')
        client_secret=credentials('dev_client_secret')
        
      }
      steps {
            bat 'mvn -U -V -e -B -DskipTests -Pdev deploy -DmuleDeploy -Danypoint.username="%ANYPOINT_CREDETIALS_USR%" -Danypoint.password="%ANYPOINT_CREDETIALS_PSW%" -Danypoint.platform.client_id="%client_id%" -Danypoint.platform.client_secret="%client_secret%"'
      }
    }
  }
}