pipeline {
  agent none
  stages {
    stage('Build Servers Parallelly') {
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

    stage('Configure-IQuote-Eflow-Server') {
      steps {
        build(job: 'Configure-IQuote-Eflow-Server', propagate: true, wait: true)
      }
    }

  }
}