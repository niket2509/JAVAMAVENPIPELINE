pipeline {
    agent any
    tools{
        maven "MAVEN"
    }

    stages {
        stage(' build') {
            steps {
                echo 'Hello World'
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/niket2509/JAVAMAVENPIPELINE.git']]])
                bat '''mvn -Dmaven.test.failure.ignore=true clean package'''
            }
        }
    }
    post{
        always{
            junit(
                allowEmptyResults:true,
                testResults: '*test-reports/.xml'
                )
        }
    }

}
