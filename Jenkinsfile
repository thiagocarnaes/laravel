node('php'){
    stage('Clean'){
        deleteDir()
        sh 'ls -la'
    }
    
    stage('Fetch') {
        checkout scm
    }
    
    stage('Build'){
        sh 'composer install --no-scripts --prefer-dist --no-dev --ignore-platform-reqs'
    }
    
    //stage('config') {
    //    parallel(
    //        'config cache': {
    //            echo 'Tarefa paralela 01' 
    //        },
    //        'config route': {
    //            echo 'Tarefa Paralela 02'
    //        }
    //    )
    //}
    stage('Docker Build') {
        sh 'docker build -t tcarnaes/laravel:$BUILD_NUMBER .'
    }
    
    stage('Docker Ship') {
        sh 'docker push tcarnaes/laravel:$BUILD_NUMBER'
        sh 'docker rmi -f tcarnaes/laravel:$BUILD_NUMBER'
    }
}
