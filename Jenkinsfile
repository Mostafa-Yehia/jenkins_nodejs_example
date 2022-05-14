pipeline {
  agent any
  stages {
    stage('Docker Build') {
      agent any
      steps {
        sh 'docker build -t mostafaye7ia/nodejs .'
      }
    }
    stage('Docker Push') {
      agent any
      steps {
        withCredentials([usernamePassword(credentialsId: 'docker', passwordVariable: 'pass', usernameVariable: 'user')]) {
          sh "docker login -u ${env.user} -p ${env.pass}"
          sh 'docker push mostafaye7ia/nodejs'
        }
      }
    }
    stage('Docker run') {
      agent any
      steps {
          sh 'docker run -p 3000:3000 mostafaye7ia/nodejs'
      }
    }
  }
}
