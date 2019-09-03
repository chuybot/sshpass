pipeline {
  agent any
  stages {
    stage('Simple Test') {
      when {
          branch 'master'
      }
      steps {
        sh 'echo wooow'
      }
    }
    stage('change') {
      steps {
        sh "echo a> a"
        sh "git add a"
        sh "git commit -m 'Add extra character'"
        withCredentials([usernamePassword(credentialsId: '7d6064c2-591d-41d1-a92a-fc26b9c7cd64', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
            sh "git"
            sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@<REPO> origin HEAD"
        }
        script{
          if (env.CHANGE_ID == null) { echo "got a null change_id"}
        }
        echo "change"
      }
    }
  }
}
