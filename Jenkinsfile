pipeline {
     
     agent {
          docker {
               image 'maven:3-jdk-11'  
               args '-p 33333:8080' 
          }
     }
     environment {
          HOME = '.'
     }

     
     
     stages {
          stage('Source') {
               steps {
                    git branch: 'main',
                        url: 'https://github.com/ladyusa/wisdom-book-demo'
               }
          }
          stage('Build') {
               steps {
                    sh 'mvn package -DskipTests'
               }
          }
          stage('Test') {
               steps {
                    echo 'testing...'
                    //sh 'mvn test'
               }
          }
          stage('Deploy') {
               steps {
                    sh 'java -jar ./target/book-0.0.1-SNAPSHOT.jar'
               }
          }
     }
}
