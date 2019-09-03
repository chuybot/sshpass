pipeline {
    agent {
        label "abc"
    }
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
        sh "echo 'a' >>a"
        sh "git add a"
        sh "git config user.name 'Intel Kubernetes CI/CD Robot'"
        sh "git config user.email 'k8s-bot@intel.com'"
        sh "git commit -s -m 'Add character'"
        sh "git remote set-url origin git@github.com:chuybot/sshpass.git"
        sh "git remote -v"
    //    sshagent(['9b2359bb-540b-4df3-a4b7-d304a426b2db']) {
      //    sh "git push origin HEAD"
       // }
          withCredentials([sshUserPrivateKey(credentialsId: '9b2359bb-540b-4df3-a4b7-d304a426b2db', keyFileVariable: 'SSH_KEY')]) {
   sh("git push origin HEAD")
}
//        withCredentials([usernamePassword(credentialsId: '7d6064c2-591d-41d1-a92a-fc26b9c7cd64', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
  //          
    //        sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/chuybot/sshpass.git origin HEAD"
      //  }
        script{
          if (env.CHANGE_ID == null) { echo "got a null change_id"}
        }
        echo "change"
      }
    }
  }
}
