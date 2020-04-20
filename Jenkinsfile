node('docker') {

    stage 'Checkout'
        checkout scm
    stage 'Build'
    sh "docker build -t accountownerapp:B${BUILD_NUMBER} -f Dockerfile ."
    
    stage 'UnitTest'
    sh "docker build -t accountownerapp:test-B${BUILD_NUMBER} -f Dockerfile.Integration ."
}
