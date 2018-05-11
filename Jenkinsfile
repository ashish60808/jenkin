pipeline {
    agent any
    stages {
        stage('Perf test') {
            steps {
            bat 'jmeter.bat -n -t C:\\LoadTools\\apache-jmeter-4.0\\bin\\examples\\Demo.jmx -JUsers=1 -JRampUp=1 -JDuration=500 -l Results.jtl -e -o Jmeter'
                
            }            
        }
    }


     post {
        success {
          // publish html
          publishHTML target: [
              allowMissing: false,
              alwaysLinkToLastBuild: false,
              keepAll: true,
              reportDir: 'Jmeter',
              reportFiles: 'index.html',
              reportName: 'Perfomance Test Report'
            ]
        }
      }
}
