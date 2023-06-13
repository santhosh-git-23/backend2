pipeline {
    agent any
    tools {
    maven 'maven' 
    }
    triggers {
    pollSCM '* * * * *'
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Deploy') {
            steps {
                script {
                    def tomcatUrl = 'http://16.170.224.112:8080/' // Replace with your Tomcat URL
                    def tomcatUser = 'admin' // Replace with your Tomcat username
                    def tomcatPass = 'admin' // Replace with your Tomcat password
                    def warFileName = '**/*.war' // Replace with your WAR file name
                    
                    def tomcatDeployUrl = "$http://16.170.224.112:8080//manager/text/deploy?path=/&update=true"
                    def authHeader = "Basic " + "$admin:$admin".bytes.encodeBase64().toString()

                    sh "curl -v --user '$admin:$admin' --upload-file $**/*.war $http://16.170.224.112:8080/"
                }
            }
        }
    }
}
