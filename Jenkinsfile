pipeline {
agent any
tools {
maven 'Maven' jdk 'JDK21' }
stages {
stage('Checkout') {
steps {
checkout scm
}
}
stage('Build') {
steps {
script {
if (isUnix()) {
sh 'mvn clean compile'
} else {
bat 'mvn clean compile'
}
// Must match Jenkins Global Tool Configuration
// Configure this as JDK 21 in Jenkins
}
}
}
stage('Test') {
steps {
script {
if (isUnix()) {
sh 'mvn test'
} else {
bat 'mvn test'
}
}
}
}
}
post {
always {
}
junit '**/target/surefire-reports/*.xml'
}
}
