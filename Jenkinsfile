node {
    def app

    stage('Clone repository') {
      

        checkout scm
    }

    stage('Update GIT') {
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    withCredentials([usernamePassword(credentialsId: 'github', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                        //def encodedPassword = URLEncoder.encode("$GIT_PASSWORD",'UTF-8')
                        sh "git config user.email singhkaran9830@gmail.com"
                        sh "git config user.name darthvader30"
                        //sh "git switch master"
                        sh "cat deployment.yaml"
                        sh "sed -i 's+darthvader4/eks-demo.*+darthvader4/eks-demo:${DOCKERTAG}+g' deployment.yaml"
                        sh "cat deployment.yaml"
                        sh "git add ."
                        sh "git commit -m 'Done by Jenkins Job changemanifest: ${env.BUILD_NUMBER}'"
                        // sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/eks-manifest.git HEAD:main"
                        sh "git push https://darthvader30:${GIT_PASSWORD}@github.com/darthvader30/eks-manifest.git HEAD:main"
      }
    }
  }
}
}
