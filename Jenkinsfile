pipeline {
    agent any
    stages {
        stage ('Build') {
            steps {script {
                    sh 'mvn clean install'
            }   
            }
            }
        stage('Build image') {
            steps {   
            script{
        /* This builds the actual image */
        sh 'docker build . -t  benstucke/workbench'
        echo '$IBM_CREDENTIAL'
        echo 'app: $app'
        sh 'cf login -a https://api.eu-de.cf.cloud.ibm.com -c $IBM_CREDENTIAL'
        sh 'cf t -o "adesso Chatbot Workbench und Runtime" -s QA'
        sh 'ibmcloud cf push cicd-jenkins-example --docker-image benstucke/workbench'
            }
    }
        
    }
}
}