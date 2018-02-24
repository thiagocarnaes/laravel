node('php'){
    stage('Clean'){
        deleteDir()
        sh 'ls -la'
    }
    
    stage('Fetch') {
        checkout scm
    }
    
    stage('Docker Build') {
        sh 'docker build -t tcarnaes/laravel:$BUILD_NUMBER .'
    }
    
    stage('Docker Ship') {
        sh 'docker push tcarnaes/laravel:$BUILD_NUMBER'
    }
}
