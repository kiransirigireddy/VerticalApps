pipeline {
  agent none
  stages {
    stage('Build Vertical Apps Environment') {
      parallel {
        stage('Build Print Flow Server') {
          steps {
            build(job: 'VApps-PrintFlow', quietPeriod: 3)
          }
        }

        stage('Build IQuote Server') {
          steps {
            build(job: 'VApps-IQuote', quietPeriod: 3)
          }
        }

        stage('Build AC4D Server') {
          steps {
            build(job: 'VApps-AC4D', quietPeriod: 3)
          }
        }

      }
    }

    stage('Configure- IQuoteandEflowServer') {
      steps {
        build 'Configure-IQuote-Eflow-Server'
      }
    }

  }
}