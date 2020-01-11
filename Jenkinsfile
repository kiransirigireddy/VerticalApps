pipeline {
  agent none
  stages {
    stage('Environment') {
      parallel {
        stage('Prepare -Environment') {
          steps {
            build(job: 'Spin_VM-or-Contanier-1', quietPeriod: 2)
          }
        }

        stage('Download Docker Image with Pre-req') {
          steps {
            build(job: 'Build Docker Image - A', quietPeriod: 2)
          }
        }

      }
    }

    stage('Build') {
      parallel {
        stage('Pull Source Code-GIT') {
          steps {
            build(job: 'PullSourceCode', quietPeriod: 2)
          }
        }

        stage('Build Maven') {
          steps {
            build(job: 'BuildMaven', quietPeriod: 2)
          }
        }

        stage('JUnit Test') {
          steps {
            build(job: 'JunitTest', quietPeriod: 3)
          }
        }

        stage('Jacoco Code Coverage') {
          steps {
            build(job: 'JacocoCodeCoverage', quietPeriod: 3)
          }
        }

        stage('Sonar Cube Analysis') {
          steps {
            build(job: 'SonarCubeAnalysis', quietPeriod: 3)
          }
        }

      }
    }

    stage('Deploy') {
      parallel {
        stage('Build Product A Docker Image') {
          steps {
            build(job: 'Install Product A', quietPeriod: 2)
          }
        }

        stage('Build Product B Docker Image') {
          steps {
            build 'Install Product B'
          }
        }

        stage('Build Product C Docker Image') {
          steps {
            build(job: 'Install Product C', quietPeriod: 3)
          }
        }

        stage('Spin Container - Product A') {
          steps {
            build(job: 'Build Docker Image - A', quietPeriod: 2)
          }
        }

        stage('Spin Container - Product B') {
          steps {
            build(job: 'Build Docker Image - A', quietPeriod: 2)
          }
        }

        stage('Spin Container - Product C') {
          steps {
            build(job: 'Build Docker Image - A', quietPeriod: 2)
          }
        }

      }
    }

    stage('Product Integration') {
      parallel {
        stage('Integrate Product-A') {
          steps {
            build(job: 'IntegrateProduct-A', quietPeriod: 2)
          }
        }

        stage('Integrate Product-B') {
          steps {
            build(job: 'IntegrateProduct-B', quietPeriod: 2)
          }
        }

        stage('Integrate Product-C') {
          steps {
            build 'IntegrateProduct-C'
          }
        }

      }
    }

    stage('Functional Test') {
      parallel {
        stage('Selenium Test - Firefox') {
          steps {
            build(job: 'Selenium Test - Firefox', quietPeriod: 2)
          }
        }

        stage('Selenium Test - Chrome') {
          steps {
            build(job: 'Selenium Test - Chrome', quietPeriod: 2)
          }
        }

        stage('Selenium Test - IE') {
          steps {
            build(job: 'Selenium Test - IE', quietPeriod: 2)
          }
        }

      }
    }

    stage('Non Functional Test') {
      parallel {
        stage('Performance Test - Jmeter') {
          steps {
            build(job: 'PerformanceTest-Jmeter', quietPeriod: 2)
          }
        }

        stage('OWASP-ZAP Security Test') {
          steps {
            build(job: 'OWASP-ZAPSecurityTest', quietPeriod: 2)
          }
        }

      }
    }

    stage('Publish the Docker Images') {
      parallel {
        stage('Publish Product Docker Image  - A') {
          steps {
            build(job: 'PublishBuild-A', quietPeriod: 2)
          }
        }

        stage('Publish Product Docker Image  - B') {
          steps {
            build(job: 'PublishBuild-B', quietPeriod: 2)
          }
        }

        stage('Publish Product Docker Image  - C') {
          steps {
            build(job: 'PublishBuild-C', quietPeriod: 2)
          }
        }

      }
    }

  }
}