# code
git code
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Git Commands</title>
</head>
<body>
    <h1>Git Commands for Project Setup</h1>

    <p>Initialize Git repository:</p>
    <pre>
        git init
        git remote add origin https://github.com/your_username/your_repository.git
        git add .
        git commit -m "Initial commit"
        git push -u origin main
    </pre>

    <p>Create Maven project:</p>
    <pre>
        mvn archetype:generate \
            -DgroupId=com.example \
            -DartifactId=my-app \
            -DarchetypeArtifactId=maven-archetype-quickstart \
            -DinteractiveMode=false
    </pre>

    <p>Sample Jenkins Pipeline Script:</p>
    <pre>
        pipeline {
            agent any

            stages {
                stage('Build') {
                    steps {
                        sh 'mvn clean package'
                    }
                }
                stage('Deploy to Tomcat') {
                    steps {
                        sh 'cp target/*.war /path/to/tomcat/webapps/'
                    }
                }
                stage('Deploy to Nexus') {
                    steps {
                        nexusArtifactUploader(
                            nexusVersion: 'nexus3',
                            protocol: 'http',
                            nexusUrl: 'http://your-nexus-url/repository/maven-releases/',
                            groupId: 'com.example',
                            version: '1.0',
                            repository: 'maven-releases',
                            credentialsId: 'your-nexus-credentials',
                            artifacts: [
                                [artifactId: 'my-app', type: 'war']
                            ]
                        )
                    }
                }
            }
        }
    </pre>

    <p>Make sure to replace placeholders (like your_username, your_repository, etc.) with your actual details.</p>

</body>
</html>

