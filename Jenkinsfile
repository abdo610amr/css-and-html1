pipeline {
    agent any

    environment {
        FIREBASE_PROJECT = "taskcloud-a1c18"
        GOOGLE_APPLICATION_CREDENTIALS = "${WORKSPACE}\\firebase-key.json"
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Load Firebase Key') {
            steps {
                withCredentials([file(credentialsId: 'firebase-key', variable: 'FB_KEY')]) {
                    bat 'copy "%FB_KEY%" "%GOOGLE_APPLICATION_CREDENTIALS%"'
                }
            }
        }

        stage('Deploy to Firebase Hosting') {
            steps {
                bat '"C:\\Users\\VICTUS\\AppData\\Roaming\\npm\\firebase.cmd" deploy --only hosting --project %FIREBASE_PROJECT%'
            }
        }
    }
}
