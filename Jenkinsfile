pipeline {
    agent any

    environment {
        ANDROID_HOME = '/home/idrbt/Android/Sdk'  // Set the path to your Android SDK
        PATH = "${ANDROID_HOME}/tools/bin:${PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Set Up Environment') {
            steps {
                script {
                    sh 'chmod +x gradlew'  // Ensure the gradlew script has execute permissions
                    sh './gradlew dependencies'  // Download dependencies
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    sh './gradlew assembleDebug'  // Adjust the task based on your build configuration
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    sh './gradlew test'  // Adjust the task based on your test configuration
                }
            }
        }

        // Add more stages as needed, such as deploying to a test or production environment
    }

   // post {
     //   success {
            // Perform actions when the build is successful
      //  }
     //   failure {
            // Perform actions when the build fails
     //   }
//    }
}
