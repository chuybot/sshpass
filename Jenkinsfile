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
        script{
          if (env.CHANGE_ID == null) { echo "got a null change_id"}
        }
        echo "change"
      }
    }
  }
}
