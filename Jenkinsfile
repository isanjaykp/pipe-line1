pipeline {
environment {
    BRANCH_NAME = "${env.BRANCH_NAME}"
}
agent any
stages{
    stage('Build-Initiator-Info'){
            steps{
                sh 'echo "Send Info "'
                
            }
    }
    stage('Build') {
        steps{
             catchError {
                sh 'echo "This is build"'
            }
         }
         post {
            success {
                echo 'Compile Stage Successful . . .'
            }
            failure {
                echo 'Compile stage failed'
                error('Stopping early…')

             }
    }
   }
  stage ('Deploy To Prod'){
  input{
    message "Do you want to proceed for production deployment?"
  }
    steps {
                sh 'echo "Deploy into Prod"'

              }
        }
stage('build2') {
        steps {
            sh  """
                # Some commands
                """
            script {
              timeout(time: 10, unit: 'MINUTES') {
                input(id: "Deploy Gate", message: "Deploy ${params.project_name}?", ok: 'Deploy')
              }
            }
        }
    }

stage('deploy2') {
        when {
            branch 'master'
        }
        steps {
            sh  """
                # some commands
                """
        }
    }
}
}
