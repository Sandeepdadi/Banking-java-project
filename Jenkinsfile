pipeline {
  agent any

  stages {
    stage('checkout the code from github') {
      steps {
        echo "github url checkout"
        git url: 'https://github.com/Sandeepdadi/Banking-java-project.git', branch: 'master'
      }
    }

    stage('codecompile with akshat') {
      steps {
        echo "starting compiling"
        sh 'mvn compile'
      }
    }

    stage('codetesting with akshat') {
      steps {
        sh 'mvn test'
      }
    }

    stage('qa with akshat') {
      steps {
        sh 'mvn checkstyle:checkstyle'
      }
    }

    stage('package with akshat') {
      steps {
        sh 'mvn package'
      }
    }

    stage('run dockerfile') {
      steps {
        sh 'docker build -t myimg .'
      }
    }

    stage('port expose') {
      steps {
        sh '''
          docker rm -f c000 || true
          docker run -dt -p 8091:8091 --name c000 myimg
        '''
      }
    }
  }
}

