pipeline {
    agent any
    
    stages{
        stage ('Checkout Code') {
            steps{
                echo "Clone the code from git"
                //git url:"https://github.com/LondheShubham153/django-notes-app.git", branch: "main"
                git url: "https://github.com/Ramesh1984-10/django-notes-app.git", branch: "main"
            }
        }
        
        stage ('Build code') {
            steps{
                echo "Build docker image"
                sh "docker build -t myimage ."
            }
        }
        stage ('Push the docker image') {
            steps{
                echo "Push the docker image to docker hub"
                sh "docker tag myimage rameshk1984/myimage:latest"
                withCredentials([usernamePassword(credentialsId:"dockercred",passwordVariable:"dockerpass",usernameVariable:"dockeruser")]){
                sh "docker login -u ${env.dockeruser} -p ${env.dockerpass}" 
                sh "docker push rameshk1984/kubernetesproject:latest"
                }
               
            }
        }
        // stage ('Deploy') {
        //     steps{
        //         echo "Deploy the  docker image"
        //         sh "docker-compose down && docker-compose up -d"
        //     }
        // }
    }
}













// pipeline {
//     agent any 
    
//     stages{
//         stage("Clone Code"){
//             steps {
//                 echo "Cloning the code"
//                 git url:"https://github.com/LondheShubham153/django-notes-app.git", branch: "main"
//             }
//         }
//         stage("Build"){
//             steps {
//                 echo "Building the image"
//                 sh "docker build -t my-note-app ."
//             }
//         }
//         stage("Push to Docker Hub"){
//             steps {
//                 echo "Pushing the image to docker hub"
//                 withCredentials([usernamePassword(credentialsId:"dockerHub",passwordVariable:"dockerHubPass",usernameVariable:"dockerHubUser")]){
//                 sh "docker tag my-note-app ${env.dockerHubUser}/my-note-app:latest"
//                 sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPass}"
//                 sh "docker push ${env.dockerHubUser}/my-note-app:latest"
//                 }
//             }
//         }
//         stage("Deploy"){
//             steps {
//                 echo "Deploying the container"
//                 sh "docker-compose down && docker-compose up -d"
                
//             }
//         }
//     }
// }



