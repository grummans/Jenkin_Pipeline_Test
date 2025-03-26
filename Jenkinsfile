pipeline{
  agent any
  stages{
    stage('Checkout'){
      steps{
        checkout([
                    $class: 'GitSCM',
                    branches: [[name: '*/develop']],
                    extensions: [],
                    userRemoteConfigs: [[
                        url: 'http://gitlab.idpass.kr/winwintek/university/kaywon.curr/kaywon.curr.backend.git',
                        credentialsId: 'gitlab-pat'  // ID credential chứa PAT
                    ]]
                ])
      }
    }
    stage('Build'){
      steps{
        echo 'Build step'
      }
    }
  }
}
