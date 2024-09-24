pipeline {
    agent { label "node" }

    stages {
        stage('Stage1-cloning project') {
            steps {
                echo 'cloning project from git'
                git 'https://github.com/kogile-marakini/Helloworld-latest.git'
            }
        }
        stage('Stage2 -maven build') {
            steps {
                echo 'Maven build'
                sh 'yum install maven -y'
                sh 'mvn clean package'
            }
        }
              
                
        stage('Stage3-docker build') {
            steps {
                echo 'Stage3-docker build'
                sh 'docker build -t mywebsite .'
            }
        }
        stage('Stage4-Tag image') {
            steps {
                echo 'Tag image with account Kmarakini'
                sh 'docker tag mywebsite Kmarakini/mywebsite'
            }
        }
        stage('Stage5-deploy to dockerhub') {
            steps {
                echo 'deploy to dockerhub'
                sh 'docker login -u Kmarakini -p Mydockerpwd@1'
                sh 'docker push Kmarakini/mywebsite'
            }
        }
        stage('Stage7-run_my_dockerimage') {
            steps {
                echo 'Stage6-run_my_dockerimage'
                sh 'docker run --name mywebsite_container -d -p 8181:8080 Kmarakini/mywebsite'
            }
        }
         
    }
}
