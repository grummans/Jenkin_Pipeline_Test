pipeline{
  agent {
    docker {
      image 'gradle:8.4-jdk17'
      args '-v $HOME/.gradle:/home/gradle/.gradle'
    }
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
    stage('Build'){
      steps{
        echo 'Build step'
      }
    }
  }
}
