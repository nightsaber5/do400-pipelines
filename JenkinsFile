node('nodejs') {
    stage('Checkout') {
        git branch: 'main',
            url: 'https://github.com/nightsaber5/do400-pipelines'
    }
    stage('Backend Tests') {
        sh 'node ./backend/test.js'
    }
    stage('Frontend Tests') {
        sh 'node ./frontend/test.js'
    }
}