pipeline {
  agent none
  stages {
    stage('Containers/VM from Image/Templates') {
      parallel {
        stage('Deploy VM1 from Template1') {
          steps {
            sleep 1
          }
        }

        stage('Deploy VM2 from Template2') {
          steps {
            sleep 1
          }
        }

        stage('Deploy VM3 from Template3') {
          steps {
            sleep 1
          }
        }

      }
    }

    stage('Deploy Products') {
      parallel {
        stage('Deploy Product A') {
          steps {
            sleep 1
          }
        }

        stage('Deploy Product 2') {
          steps {
            sleep 1
          }
        }

        stage('Deploy Product C') {
          steps {
            sleep 1
          }
        }

      }
    }

  }
}