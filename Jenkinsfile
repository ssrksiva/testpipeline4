pipeline {
  agent any
  stages {
    stage('Pull') {
      steps {
        git(url: 'https://github.com/ssrksiva/testpipeline4.git', branch: 'develop', poll: true)
      }
    }

    stage('Check Java') {
      steps {
        sh 'java -version'
      }
    }

    stage('Deliver for development') {
      when {
        branch 'develop'
      }
      steps {
        sh 'git config --global user.name "ssrksiva"'
        sh 'git config --global user.email "sssrkbsc@gmail.com"'
        sh 'git merge -s ours develop --allow-unrelated-histories'
        sh 'git config --global credential.username ssrksiva'
        sh 'git config --global credential.password 14Dec@1991'
        withCredentials(bindings: [usernamePassword(credentialsId: 'testgithubcred', usernameVariable: 'user', passwordVariable: 'pass')]) {
          script {
            env.encodedPass=URLEncoder.encode(pass, "UTF-8")
          }

          sh 'git push https://${user}:${encodedPass}@github.com/${user}/testpipeline4.git HEAD:master -f'
        }

      }
    }

  }
}