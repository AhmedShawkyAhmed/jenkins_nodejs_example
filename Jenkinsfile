pipeline {
    agent any


    stages {
        stage('preparation') {
            steps {
                
                // Get some code from a GitHub repository
                git 'https://github.com/AhmedShawkyAhmed/Booster_CI_CD_Project.git'
            }

        }
        stage('docker build') {
            steps {
                
                // Get some code from a GitHub repository
                withCredentials([usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                sh """
                   docker build . -f dockerfile -t ahmedshawky21/sprints_jenkins_course:latest
                   docker login -u ${USERNAME} -p ${PASSWORD}
                   docker push ahmedshawky21/sprints_jenkins_course:latest
                """
            }
            }
        }     
        stage('deployment') {
            steps {
                
                // Get some code from a GitHub repository
                sh"""
                   docker run -d -p 3000:3000 ahmedshawky21/sprints_jenkins_course:latest
                   """

            }
        }         
    }
}
