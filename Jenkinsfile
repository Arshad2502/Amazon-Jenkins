pipeline {
    agent any
    environment {
        // Use PATH+EXTRA to append to PATH properly
        PATH = "/usr/bin:/bin:/opt/homebrew/bin"
    }
    stages {

        stage('pull scm') {
            steps {
                git branch: 'main', url: 'https://github.com/PraveenKuber/Amazon-Jenkins.git'
            }
        }

        stage('validate') {
            steps {
                sh 'mvn validate'
            }
        }

        stage('compile') {
            steps {
                sh 'mvn compi'
            }
        }
        stage('test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('package') {
            steps {
                sh 'mvn package'
            }
        }
        stage('verify') {
            steps {
                sh 'mvn verify'
            }
        }
        stage('build') {
            steps {
                 sh 'mvn clean install'
            }
        }

        
    }

  post{

  success{
     echo 'Build success'
  }
    
  failure{
       echo 'Failure in the build'
   }

   unstable {
      echo 'Build is unstable.'
    }
    aborted {
      echo 'Build was aborted.'
    }
    always {
      echo 'This always runs.'
    }
  }


}
