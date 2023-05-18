@@ -1,29 +1,28 @@
pipeline {
    agent { label 'dev-agent' }

    agent { label "dev-server" }
    stages{
        stage('Code'){
            steps {
                git url: 'https://github.com/TajarThot/node-todo-cicd.git', branch: 'master'
        stage("Clone Code"){
            steps{
                git url: "https://github.com/TajarThot/node-todo-cicd.git", branch: "master"
            }
        }
        stage('Build and Test'){
            steps {
                sh 'docker build . -t TajarThot/node-todo-app-cicd:latest' 
        stage("Build and Test"){
            steps{
                sh "docker build . -t node-app-test-new"
            }
        }
        stage('Login and Push Image'){
            steps {
                echo 'logging in to docker hub and pushing image..'
                withCredentials([usernamePassword(credentialsId:'dockerHub',passwordVariable:'dockerHubPassword', usernameVariable:'dockerHubUser')]) {
                    sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
                    sh "docker push trainwithshubham/node-todo-app-cicd:latest"
        stage("Push to Docker Hub"){
            steps{
                withCredentials([usernamePassword(credentialsId:"dockerHub",passwordVariable:"dockerHubPass",usernameVariable:"dockerHubUser")]){
                sh "docker tag node-app-test-new ${env.dockerHubUser}/node-app-test-new:latest"
                sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPass}"
                sh "docker push ${env.dockerHubUser}/node-app-test-new:latest"
                }
            }
        }
        stage('Deploy'){
            steps {
                sh 'docker-compose down && docker-compose up -d'
        stage("Deploy"){
            steps{
                sh "docker-compose down && docker-compose up -d"
            }
        }
    }
}
