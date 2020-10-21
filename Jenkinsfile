pipeline {
environment {
registry = "ishita31/midwebapp"
registryCredential = 'ishitadockerid'
dockerImage = ''
}
agent any
stages {
stage('Cloning our Git') {
steps {
git 'https://github.com/ishitasinghal/Python-Student-Database-Management-System.git'
}
}
stage('Build') {
steps {
sh 'docker build -t sample-web-app .'
}
}
stage('Building our image') {
steps{
script {
dockerImage = docker.build registry + ":$BUILD_NUMBER"
}
}
}
stage('Deploy our image') {
steps{
script {
docker.withRegistry( '', registryCredential ) {
dockerImage.push()
}
}
}
}
}
}
