pipeline {
    node {
        stage("clone git repo") {
            git 'https://github.com/dzmitrydan/shopizer-jmeter-test.git'
        }
        stage("run test") {
            sh "jmeter -n -t /shopizer_test_plan.jmx -l /reports/shopizer_test_result.csv -e -o /reports/HTMLReport/"
        }
        stage('publish results') {
            sh "mv /tmp/reports/* $WORKSPACE/$BUILD_NUMBER/"
            archiveArtifacts artifacts: '$WORKSPACE/$BUILD_NUMBER/JMeter.jtl, $WORKSPACE/$BUILD_NUMBER/HtmlReport/index.html'
        }
    }
}