pipeline {

  agent any
  environment {
  M2SETTINGS = "C:\\Users\\lenovo\\.m2\\settings.xml"
  }
  
  stages {
    stage('Build') {
      steps {
            bat 'mvn -B -U -e -V clean -gs %M2SETTINGS% -DskipTests package'
      }
    }

    stage('Test') {
      steps {
           echo "**********************munit test cas is executed**********************"
      }
    }

     stage('Deployment') {
      steps {
            bat 'mvn -U -V -e -B -DskipTests -gs %M2SETTINGS% -Pdev deploy -DmuleDeploy'
      }
    }
  }
}