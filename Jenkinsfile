pipeline {
    agent any
    tools {
        maven 'MAVEN'
        jdk 'JDK17'
    }
     environment {
        NAME = "Alan"
    }

    stages {
        stage('Declarative') {
             steps {
                echo "Jenkins Pipeline using the declarative script"
             }
        }
        stage('Clone') {
            steps {
                echo 'Clone Started'
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/smittank78/Jenkins-Pipeline-Aop.git']])
                echo 'Clone Finished...'
            }
            post{
                success
                {
                    sh "mvn clean install"
                    echo 'maven clean and install completed'
                }
            }
        }
        stage('Build') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                    echo "JAVA_HOME = ${JAVA_HOME}"
                    '''
                echo 'Build Processing...'
            }
        }
        stage('Test') {
            steps {
                echo 'Test Started...'
                sh "mvn test"
                echo 'Test Completed...'
            }
            
        }
        
        
        stage('Release') {

            steps {
                echo 'Release Started...'
                echo "NAME = ${env.NAME}"
                echo 'Release Processing...'
            }
        }

    }
}
