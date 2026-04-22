stage('Push to Docker Hub') {
    steps {
        withCredentials([usernamePassword(credentialsId: 'dockerhub-creds',
                                          usernameVariable: '2024ht66055',
                                          passwordVariable: '123456789')]) {
            bat '''
            docker login -u %USER% -p %PASS%
            docker push 2024ht66055/appv1:v2
            '''
        }
    }
}
