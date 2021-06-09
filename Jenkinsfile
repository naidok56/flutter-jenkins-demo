pipeline {
    agent any
        
    stages {
        stage('GIT PULL') {
            steps {
                git branch: "main", url: 'https://github.com/naidok56/flutter-jenkins-demo.git'
            }
        }
        stage ('Flutter Doctor') {
            steps {
                withEnv(['PATH+EXTRA=/usr/sbin:/usr/bin:/sbin:/bin']) {
                sh "flutter doctor -v"
                }
            }
        }
        stage('BUILD') {
            steps {
                withEnv(['PATH+EXTRA=/usr/sbin:/usr/bin:/sbin:/bin']) {  
                sh 'flutter build apk'
             }
                
            }
        }
        stage('Distribute Android APK') {
              steps {
                  appCenter apiToken: 'f9789718700a0e7cddf63ac22f6dee769ac22a4b',
                          ownerName: 'kylen.zn-gmail.com',
                          appName: 'JenkinsFlutterDemoAnd',
                          pathToApp: 'build/app/outputs/apk/release/app-release.apk',
                          distributionGroups: 'Testers'
              }
        }
    }
}
