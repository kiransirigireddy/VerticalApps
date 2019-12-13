pipeline {
  agent {
    node {
      label 'PFlow-VApps'
    }

  }
  stages {
    stage('Build Print Flow Server') {
      parallel {
        stage('Build Print Flow Server') {
          steps {
            build(job: 'VApps-PrintFlow', propagate: true, quietPeriod: 3, wait: true)
            powershell 'Remote Connection to PF Server'
          }
        }

        stage('Build IQuote Server') {
          steps {
            build(job: 'VApps-IQuote', propagate: true, quietPeriod: 3, wait: true)
          }
        }

        stage('Build AC4D Server') {
          steps {
            build(job: 'VApps-AC4D', propagate: true, quietPeriod: 3, wait: true)
          }
        }

      }
    }

  }
}