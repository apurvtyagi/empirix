pipeline {

 agent any

 stages {

  stage("get parameters from user") {
   steps {
    script {
     // Variables for input
     def dir_name = input(
      id: 'dir_name', message: 'Enter Dir Path):?',
      parameters: [
       [$class: 'StringParameterDefinition', defaultValue: 'None', description: 'List of tags', name: 'dir_nameList'],
      ]
     )
     env.dir = "${dir_name}"
    }
   }
  }
  stage("build") {
   steps {
    echo "Build Path is: ${env.dir}"
    dir("${env.dir}") {

     checkout scm: [$class: 'GitSCM', userRemoteConfigs: [
      [url: '${git_url}', credentialsId: 'be22b56d-5a60-4829-8a05-164ac9ef211f']
     ], branches: [
      [name: "master"]
     ]], poll: 'false'

    }
   }
  }
 }
}
