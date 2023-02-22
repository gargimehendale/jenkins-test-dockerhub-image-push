pipeline {
  agent any
   tools {
    maven 'maven'
    jdk 'java'
   }
   environment {
    dockerhub=credentials('dockerhub')
   }
  stages{
   stage('build image')
   {
    when{
      branch "prod"
        }
    steps{
      sh 'docker build -t capstone-img:1.01 .'
         }
   }
   stage('pushing to dockerhub')
   {
    when{
      branch "prod"
     }
    steps{
      sh 'docker tag capstone-img:1.01 gargimehendale/capstone:1.01'
      sh 'echo $dockerhub_PSW | docker login -u $dockerhub_USR --password-stdin'
      sh 'docker push gargimehendale/castone:1.01'
     }
   }
}
}
