pipeline {
  agent any
    stages {
      stage ('build stage') {
        steps {
          echo "build stage is running"
        }
      }
      stage ('test stage') {
        steps {
          echo "Running test stage"
        }
      }
      stage ('Deploy Stage') {
        steps {
          echo "Runnng Deploy stage"
        }
      }
      stage ('Creating Directory') {
        steps {
          sh 'mkdir -p Amitprojects'
        }
      }
      stage ('demo.txt') {
        steps {
          sh 'echo "demo file created under Amitprojects directory" > Amitprojects/demo.txt'
        }
      }
    }
}
