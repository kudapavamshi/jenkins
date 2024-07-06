pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "MAVEN3"
    }

    stages {
        stage('DING Fetch') {
            steps {
                // Get some code from a GitHub repository
              git branch: 'main', url: 'https://github.com/kudapavamshi/jenkins.git'
            }
            post{
                success{
                    echo 'Fetch is success'
                }
            }
        }
        
         stage(' Build') {
            steps {
                // Get some code from a GitHub repository
                 sh 'mvn -B -DskipTests clean package'
            }
        }
        stage(' Test') {
            steps {
                // Get some code from a GitHub repository
                 sh 'mvn test'
            }
            post{
                success{
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
    }
}
