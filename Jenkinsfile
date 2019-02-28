pipeline {
  agent {
    label 'maven-kaniko'
  }
  libraries {
    lib('DaytraderLib')
  }
  stages {
    stage('build maven') {
        steps {
            mavenBuild('daytrader-gatewayapp')
        }
    }
        stage('Build with Kaniko') {
      environment {
        PATH = "/busybox:/kaniko:$PATH"
      }
      steps {
        kanikoBuild('kaniko',
                    'daytrader-gatewayapp',
                    'daytrader-gateway',
                    'baserepodev.devrepo.malibu-pctn.com/104017-malibu-artifacts',
                    'daytrader-example-gatewayapp',
                    'latest',
                    '4.0.0', 
                    2443)
      }
    }
  }
}
