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
        sh "git config user.name 'Intel Kubernetes CI/CD Robot'"
        sh "git config user.email 'k8s-bot@intel.com'"
        sh "git commit -m -s 'Add extra character'"
        withCredentials([usernamePassword(credentialsId: '7d6064c2-591d-41d1-a92a-fc26b9c7cd64', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
            
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
