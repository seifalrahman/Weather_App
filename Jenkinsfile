pipeline {
    agent any

    environment {
        // Set the credentials environment variable
        GITHUB_TOKEN = credentials('JenkinsWEATHERAPP')  // 'github-pat' is the ID of the stored Jenkins credential
        GITHUB_USER = 'seifalrahman' // Set your GitHub username here or use a Jenkins credential for it
        DockerHubUserName= 'seifalrahman'
        DockerHubPassword= '110011sS@'
    }

    stages {
        stage('Clone Repository') {
            steps {
                script {
                    // Construct the repository URL with the username and token
                    def repoUrl = "https://${GITHUB_USER}:${GITHUB_TOKEN}@github.com/seifalrahman/Weather_App.git"
                    def branch = 'master'

                    // Clone the repository
                    if(fileExists("./.git")){
                        sh "git pull ${repoUrl}"
                    }
                    else{
                        sh "git clone -b ${branch} ${repoUrl}"
                    }
                    
                }
            }
        }
        stage('Build Docker Image'){
            steps{
                script{
                    sh "ls"
                    sh "docker build -t myweatherapp ."
                }
            }
        }
        
        stage("Push Image to Docker Hub"){
            steps{
                script{
                    sh "docker login -u ${DockerHubUserName} -p ${DockerHubPassword}"
                    sh "docker tag myweatherapp:latest seifalrahman/weather_app:latest"
                    sh "docker push seifalrahman/weather_app:latest"
                }
            }
        }
        stage("Install Docker on VMs , Pull the image from DockerHub and run the Container"){
            steps{
                script{
                    sh "ls"
                    sh "chmod 600 ./private_key1"
                    sh "chmod 600 ./private_key2"
                    sh "export ANSIBLE_HOST_KEY_CHECKING=False"
                    sh "ansible-playbook -i inventory playbook.yml"
                }
            }
        }
    }
}
