pipeline {
    agent any

    tools {
        maven "Maven"
        jdk "JDK21"
    }

    stages {

        stage('Initialize') {
            steps {
                script {
                    if (isUnix()) {
                        sh 'echo "JAVA_HOME = $JAVA_HOME"'
                        sh 'echo "M2_HOME = $M2_HOME"'
                        sh 'echo "PATH = $PATH"'
                    } else {
                        bat 'echo "JAVA_HOME = $JAVA_HOME"'
                        bat 'echo "M2_HOME = $M2_HOME"'
                        bat 'echo "PATH = $PATH"'
                    }
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    if (isUnix()) {
                        sh 'mvn -B clean package'
                    } else {
                        bat 'mvn -B clean package'
                    }
                }
            }
        }
    }

    post {
        always {
            junit allowEmptyResults: true,
                  testResults: '**/surefire-reports/*.xml'
        }
    }
}
