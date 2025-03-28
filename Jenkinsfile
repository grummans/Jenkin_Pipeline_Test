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
            credentialsId: 'gitlab-pat'
          ]]
        ]) 
      }
    }
    stage('Test') {
      steps {
        script {
          try{
            sh './gradlew test'
            junit '/build/test-results/test/**/*.xml' 
          } catch (err) {
            error ("log:  buid/reports/tests")
          }
        } 
      }
    } 
  }
}
