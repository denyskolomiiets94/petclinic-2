pipeline {
    agent any

    stages {
        stage('git clone') {
            steps {
                cleanWs()
                git branch: 'main', url: 'https://github.com/denyskolomiiets94/petclinic-2.git'
                sh "ls -la"
            }
        }
     stage('docker build') {
            steps {
                sh "docker build -t jonnydonnybonny2112/petclinic:lates -t petclinic:lates ."
            }
        }
        stage('docker push') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker_hub_secret', passwordVariable: 'PASS', usernameVariable: 'USER')]) {
                    sh "docker login -u $user -p $pass"
                    sh "docker push jonnydonnybonny2112/petclinic:lates"
                }
            }
        }
    }
}
