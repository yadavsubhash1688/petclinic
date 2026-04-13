pipeline{
    agent none
    stages{
        stage("Checkout"){
            agent {docker 'git:latest'}
            steps{
                echo "========THIS IS A CHECKOUT STAGE========"
                git branch: 'main', url: 'https://github.com/example/repo.git'
            }
        }
        stage("Build"){
            agent {docker 'maven:3.8.4-jdk-11'
                  volumes ['/var/lib/jenkins/workspace/target:/var/jenkins_home/target']
                  }
            steps{
                echo "========THIS IS A BUILD STAGE========"
                sh 'mvn clean package'
            }
        }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}
}