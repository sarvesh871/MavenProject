pipeline {
    agent any

    tools {
        maven "MAVEN"
        jdk "JDK21"
    }

    stages {

        stage('Initialize') {
            steps {
                sh 'echo "PATH = $M2_HOME/bin:$PATH"'
                sh 'echo "M2_HOME = $M2_HOME"'
            }
        }

        stage('Build') {
            steps {
                dir('/Users/Shared/Jenkins/Home/workspace/demopipelinetask/my-app') {
                    sh 'mvn -B -DskipTests clean package'
                }
            }
        }
    }

    post {
        always {
            junit allowEmptyResults: true,
                  testResults: '**/test-reports/*.xml'
        }
    }
}
