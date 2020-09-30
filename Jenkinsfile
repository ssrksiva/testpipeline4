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
        sh 'git push https://b9e1f34cef0463191d5a3c44df0e44b17f356fb9@github.com/ssrksiva/testpipeline4.git HEAD:master -f'
      }
    }

  }
}