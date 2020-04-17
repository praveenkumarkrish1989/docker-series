node('docker') {

    stage 'Checkout'
        checkout scm
    stage 'Build'
    sh "docker build -t accountownerapp:B${BUILD_NUMBER} -f Dockerfile ."
    
    stage 'UnitTest'
    sh "docker build -t accountownerapp:test-B${BUILD_NUMBER} -f Dockerfile.Integration ."
    
         
    stage 'Integration Test'
    withEnv(['PATH = "$PATH:/usr/local/bin"']) {
        //sh 'docker-compose -f docker-compose.integration.yml up'
        sh "docker-compose -f docker-compose.integration.yml up --force-recreate --abort-on-container-exit"
        sh "docker-compose -f docker-compose.integration.yml down -v"
    }
}
