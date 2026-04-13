pipeline{
    agent any
    stages{
        stage("Checkout"){
            steps{
                echo "========THIS IS A CHECKOUT STAGE========"
                git branch: 'main', url: 'https://github.com/yadavsubhash1688/petclinic.git'
            }
        }
        stage("Build"){
            steps{
                echo "========THIS IS A BUILD STAGE========"
                sh 'mvn -version'
                sh 'mvn clean package -DskipTests -Dcheckstyle.skip=true'
            }
        }

}
}