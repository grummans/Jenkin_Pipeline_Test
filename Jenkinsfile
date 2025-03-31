pipeline{
  agent any
  stages{
    stage('Checkout'){
      steps{
        checkout([
          $class: 'GitSCM',
          branches: [[name: '*/develop']],
          extensions: [
            [$class: 'CloneOption', shallow: true, depth: 1]
          ],
          userRemoteConfigs: [[
            url: 'https://gitlab.idpass.kr/winwintek/university/kaywon.curr/kaywon.curr.backend.git',
            credentialsId: 'github-ssh'
          ]]
        ]) 
      }
    }
    stage('Test') {
      steps {
        script {
          try{
            sh 'mvn test'
          } catch (err) {
            error ("log:  buid/reports/tests")
          }
        } 
      }
    } 
  }
}
