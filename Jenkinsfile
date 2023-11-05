pipeline {
  agent {
    node {
      label 'mylinux'
    }

  }
  stages {
    stage('Build') {
      steps {
        sh 'mvn -B -DskipTests clean package'
        node(label: 'mylinux')
      }
    }

    stage('Test') {
      steps {
        sh 'mvn test'
        junit 'target/surefire-reports/*.xml'
        node(label: 'mylinux')
      }
    }

    stage('Deliver') {
      steps {
        sh './jenkins/scripts/deliver.sh'
        echo 'Hey Buddy, Build is Successful!!'
        node(label: 'mylinux')
      }
    }

  }
}