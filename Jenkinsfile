pipeline {
    agent any
       tools {
        maven 'maven-3.9.0'
        // jdk 'java'
        }

     stages {
        stage('Checkout') {
            steps {
                // git url: 'https://github.com/GitEic-Bhavin/Multibranch-Pipeline-Jave_Maven_repo.git', branch: env.BRANCH_NAME
                git branch: 'production', url: 'https://github.com/GitEic-Bhavin/Multibranch-Pipeline-Jave_Maven_repo.git'
                //    git branch: 'Maven', credentialsId: 'xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxxx', url: 'https://github.com/GitEic-Bhavin/JenkinsPrivateRepo.git'                                                                                         
            }
        }
        // stage ('Clone Repo') {
        //     steps {
        //        sh 'git clone https://github.com/GitEic-Bhavin/JenkinsPrivateRepo.git' 
        //     }
        // }
        stage('Build') {
            steps {
               sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Running App.java....'
                // sh 'javac src/main/java/com/example/App.java'
                sh 'java src/main/java/com/example/App.java'
            }
        }


        stage('Archiveartifact') {
            steps {
                archiveArtifacts artifacts: '**/target/*.jar', allowEmptyArchive: true
            }
        }
        

    }

    post {
        // always {
        //     // Steps that always run after the pipeline finishes
        //     echo 'Cleaning up...'
        //     sh 'make clean'
        // }
        success {
            // Steps that run only if the pipeline succeeds
            echo 'Pipeline succeeded!'
        }
        failure {
            // Steps that run only if the pipeline fails
            echo 'Pipeline failed!'
        }
    }
 
}
