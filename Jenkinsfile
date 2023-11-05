pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'mvn -B -DskipTests clean package'
        node(label: 'mylinuxbuild')
      }
    }

    stage('Test') {
      steps {
        sh 'mvn test'
        junit 'target/surefire-reports/*.xml'
        node(label: 'mylinuxbuild')
      }
    }

    stage('Deliver') {
      steps {
        sh './jenkins/scripts/deliver.sh'
        echo 'Hey Buddy, Build is Successful!!'
        node(label: 'mylinuxbuild')
      }
    }

  }
}