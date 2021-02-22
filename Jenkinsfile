pipeline {

  agent any
  environment {
    //adding a comment for the commit test
    DEPLOY_CREDS_USERNAME = "natcoanand_adesso_internal"
    DEPLOY_CREDS_PASSWORD = "Mani123!!"
    MULE_VERSION = '4.3.0-20201013'
    BG = "adesso SE"
    WORKER = "Micro"
  }
  stages {
    stage('Build') {
      steps {
            sh 'mvn -B -U -e -V -X clean -DskipTests package'
      }
    }

    

     stage('Deploy Development') {
      environment {
        ENVIRONMENT = 'Sandbox'
        APP_NAME = 'jenkins-deployment-test-dev'
      }
      steps {
            sh 'mvn -X -U -V -e -B -DskipTests deploy -DmuleDeploy -Dmule.version="%MULE_VERSION%" -Danypoint.username="natcoanand_adesso_internal" -Danypoint.password="Mani123!!" -Dcloudhub.app="%APP_NAME%" -Dcloudhub.environment="%ENVIRONMENT%" -Dcloudhub.bg="%BG%" -Dcloudhub.worker="%WORKER%"'
      }
    }
    

    }
    
      tools {
    maven 'mvn'
  }
  


}