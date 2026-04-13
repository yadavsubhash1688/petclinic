pipeline{
    agent none
    stages{
        stage("Checkout"){
            agent {docker {
                    image 'git:latest'}
            }
            steps{
                echo "========THIS IS A CHECKOUT STAGE========"
                git branch: 'main', url: 'https://github.com/yadavsubhash1688/petclinic.git'
            }
        }
        stage("Build"){
            agent {docker {
                    image 'maven:3.8.4-jdk-11'
                    volumes ['/var/lib/jenkins/workspace/:/var/jenkins_home/workspace/']}
                  }
            steps{
                echo "========THIS IS A BUILD STAGE========"
                sh 'mvn clean package'
            }
        }
    post{
        agent {docker {
                image 'alpine:latest'}
            }
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