pipeline {
    agent any
    tools{
        jdk 'jdk11'
        maven 'm386'
    }

    stages {
        stage('Compile') {
            steps {
             sh 'mvn compile'
            }
        }
        stage('Unit Testing') {
            steps {
             sh 'mvn test'
            }
        }
        stage('Package') {
            steps {
             sh 'mvn package'
             sh 'echo "Successful"'
            }
        }

        stage('Archive Artificat') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false
            }
        }
        stage('Publish Result'){
            steps {
                junit 'target/**/*.xml'
            }
        }

    }

}
