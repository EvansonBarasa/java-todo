pipeline { 
  agent any
   tools { 
    gradle "Gradle-6"
  }
  stages { 
    stage('clone repository') {
      steps { 
        git 'https://github.com/EvansonBarasa/java-todo.git'
      }
    }
    stage('Build project') {
      steps { 
        sh 'gradle build'
      }
    }
    stage('Tests') {
      steps { 
        sh 'gradle test'
      }
    }
    stage('Deploy to Heroku') {
     steps {
        withCredentials([usernameColonPassword(credentialsId: 'heroku', variable: 'HEROKU_CREDENTIALS' )]){
             sh 'git push https://${HEROKU_CREDENTIALS}@git.heroku.com/serene-retreat-28928.git master'
         }
        }
    } 
  }
}
