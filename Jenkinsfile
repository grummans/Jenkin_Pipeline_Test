pipeline{
  agent {
    label 'gradle-jdk17'
  }
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
        sh 'gradle clean test'  // Chạy unit test tự động
      }
      post {
        always {
          junit '**/build/test-results/test/*.xml'   
        }
      }
    } 
  }
}
