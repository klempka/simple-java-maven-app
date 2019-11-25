pipeline {
    agent {
        docker {
            image 'maven:3-alpine'
            args '-v /root/.m2:/root/.m2'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
         stage('Test') {
                    steps {
                        sh 'mvn test'
                    }
         }
         stage('Deliver') {
                     steps {
                         sh './jenkins/scripts/deliver.sh'
                     }
                 }
         stage('Development only') {
            when {
                branch 'develop'
            }
            steps {
                echo 'NO ELO TO DEVELOP'
            }
         }
         stage('Production only') {
            when {
                branch 'master'
            }
            steps {cd
                echo 'NO ELO TO PRODUCTION BEJBE'
            }
         }
         stage('Post build') {
            steps {
                echo 'POST BUILD XD'
            }
         }
    }
}