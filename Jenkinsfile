pipeline {
    agent any
    stages {
        stage("run test") {
            steps {
                sh "mvn -B clean package"
                sh "mkdir /reports"
                sh "cd /Users/Dmitry_Danilov/Desktop/Perfomance/JMeter/apache-jmeter-5.5/bin/"
                sh "jmeter -Jjmeter.save.saveservice.output_format=xml -n -t shopizer_test_plan.jmx -l reports/shopizer_test_result.jtl -e -o /reports/HTMLReport"
            }
        }
        stage('publish results') {
            steps {
                sh "mv /tmp/reports/* $WORKSPACE/$BUILD_NUMBER/"
            }

            archiveArtifacts artifacts: '$WORKSPACE/$BUILD_NUMBER/JMeter.jtl, $WORKSPACE/$BUILD_NUMBER/HtmlReport/index.html'
        }
    }
}